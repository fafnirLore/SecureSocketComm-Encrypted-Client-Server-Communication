# SecureSocketComm: Encrypted Client-Server Communication

## Project Overview

This project demonstrates a simple client-server communication system using RSA and Diffie-Hellman key exchanges with AES encryption. The server and client programs are built with Python and utilize the `socket` and `ssl` libraries for network communication and security, as well as the `cryptography` library for cryptographic operations. The system also includes a basic GUI built with Tkinter for ease of interaction.

## Features

- **Asymmetric Encryption (RSA)**
  - Secure communication using RSA for key exchange and message encryption.
- **Symmetric Encryption (AES) with Diffie-Hellman Key Exchange**
  - Secure communication using AES encryption with keys derived from a Diffie-Hellman key exchange.
- **GUI for Interaction**
  - A graphical user interface to facilitate user interaction with the server and client.

## Prerequisites

- Python 3.x
- Required libraries:
  - `socket`
  - `ssl`
  - `os`
  - `tkinter`
  - `cryptography`
  - `PIL` (for image handling in Tkinter)

## Setup

### Install Dependencies

Install the required Python libraries using pip:
```sh
pip install cryptography
pip install pillow
```

### Generate SSL/TLS Certificates

Generate a private key for the server:
```sh
openssl genpkey -algorithm RSA -out server.key
```

Create a Certificate Signing Request (CSR) for the server:
```sh
openssl req -new -key server.key -out server.csr
```

Sign the server CSR with the CA certificate to generate the server certificate:
```sh
openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out server.crt
```

Example information for `ca.crt`:
```
PEM pass phrase: 03455
Country Name: PK
State or Province Name: Punjab
Locality Name: Rawalpindi
Organization Name: FAST
Organizational Unit Name: Computing
Common Name: FARQ
Email Address: i200621@nu.edu.pk
```

### Running the Server

Run the server script:
```sh
python server.py
```

### Running the Client

Run the client script:
```sh
python client.py
```

## Usage

### Server

1. Run the server script to start the server.
2. Select the encryption method (Asymmetric or Symmetric) and enter a message to send to the client.
3. Click "Send Message" to initiate the connection and send the message.

### Client

1. Run the client script to start the client.
2. Enter a message to send to the server.
3. Click "Send Message" to initiate the connection and send the message.

## File Descriptions

### server.py

- Sets up a server that listens for incoming connections.
- Supports both RSA and Diffie-Hellman key exchanges.
- Uses AES for message encryption when using Diffie-Hellman.
- Provides a GUI for selecting encryption methods and sending messages.

### client.py

- Connects to the server and establishes a secure communication channel.
- Supports both RSA and Diffie-Hellman key exchanges.
- Uses AES for message encryption when using Diffie-Hellman.
- Provides a GUI for entering messages and viewing logs.

## Code Explanation

### Key Functions

- `generate_rsa_keypair()`: Generates an RSA key pair.
- `generate_dh_keypair()`: Generates a Diffie-Hellman key pair.
- `derive_dh_shared_key()`: Derives a shared key using Diffie-Hellman.
- `rsa_encrypt()`: Encrypts a message using RSA.
- `rsa_decrypt()`: Decrypts a message using RSA.
- `aes_encrypt()`: Encrypts a message using AES.
- `aes_decrypt()`: Decrypts a message using AES.
- `start_server()`: Starts the server and handles incoming connections.
- `start_client()`: Starts the client and connects to the server.

---
