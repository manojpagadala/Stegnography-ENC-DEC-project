Image-Based Encryption and Decryption

Introduction

This project implements an image-based encryption and decryption technique using Python. It securely embeds a secret message within an image, ensuring confidential data transmission and protection from unauthorized access.

Features

Encrypts a secret message into an image without altering its visible quality.

Uses a passcode for encryption and decryption.

Implements an end marker to ensure accurate message retrieval.

Ensures secure communication through steganography.

Technologies Used

Python for scripting and automation.

OpenCV (cv2) for image processing.

NumPy for numerical computations.

Installation & Setup

Install the required libraries:
pip install opencv-python numpy

Place the image (Temp.jpg) in the project directory.

Run the script:

python encrypt_decrypt.py

Usage

Encryption:

The script prompts for a secret message and a passcode.

It embeds the message within the image and saves it as encryptedImage.jpg.

Decryption:

The script prompts for the passcode.

If correct, it retrieves and displays the hidden message.

Example Output

Encryption

Enter secret message: GET THE KEY
Enter a passcode: 1234
Encrypted image saved as encryptedImage.jpg

Decryption

Enter passcode for decryption: 1234
Decrypted message: GET THE KEY

Future Enhancements

Enhance encryption techniques with AI-driven algorithms.

Support for multiple file formats beyond images.

Develop a cloud-based encryption and decryption service.

Create a user-friendly GUI for broader accessibility.

Author

Developed by Manoj

