import cv2
import numpy as np
import os


image_path = "Temp.jpg"
if not os.path.exists(image_path):
    print("Error: Image file not found.")
    exit()

img = cv2.imread(image_path)
if img is None:
    print("Error: Unable to read the image.")
    exit()

msg = input("Enter secret message: ")
password = input("Enter a passcode: ")

image_height, image_width, _ = img.shape
max_message_length = image_height * image_width * 3  

if len(msg) > max_message_length:
    print("Error: Message is too long for the image.")
    exit()

msg += "<END>"  
msg_index = 0

for row in range(image_height):
    for col in range(image_width):
        for channel in range(3):  
            if msg_index < len(msg):
                img[row, col, channel] = ord(msg[msg_index])  
                msg_index += 1
            else:
                break
        if msg_index >= len(msg):
            break
    if msg_index >= len(msg):
        break

encrypted_image_path = "encryptedImage.jpg"
cv2.imwrite(encrypted_image_path, img)
print(f"Encrypted image saved as {encrypted_image_path}")

os.system(f"start {encrypted_image_path}")

img = cv2.imread(encrypted_image_path)
if img is None:
    print("Error: Unable to read the encrypted image.")
    exit()

input_password = input("Enter passcode for decryption: ")

if password != input_password:
    print("Error: Incorrect passcode. Access denied.")
    exit()

decrypted_message = ""

for row in range(image_height):
    for col in range(image_width):
        for channel in range(3):
            char_val = img[row, col, channel]
            if char_val == ord('<'):  
                next_chars = ''.join([chr(img[row, col, (channel + i) % 3]) for i in range(4)])
                if next_chars == "<END>":
                    print("Decrypted message:", decrypted_message)
                    exit()
            decrypted_message += chr(char_val)

print("Decrypted message:", decrypted_message)



