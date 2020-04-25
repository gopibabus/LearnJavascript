# 🔥SSH Internals

## ⚡How SSH Works

[Credits](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work)

There are three different encryption technologies used by SSH:

1. Symmetrical encryption
2. Asymmetrical encryption
3. Hashing

### ✳Symmetrical Encryption

<img src="./assets/images/Symmetric-Encryption.png" alt="events" width="700" height="400">

* **Symmetric encryption** is a form of encryption where a secret key is used for both encryption and decryption of a message by both the client and the host.
* Symmetrical encryption is often called **shared key** or **shared secret encryption**.
* Both the client and the server derive the secret key using an agreed method, and the resultant key is never disclosed to any third party. 
* The process of creating a symmetric key is carried out by a key exchange algorithm. Key is never transmitted between the client and the host.

### ✳Asymmetrical Encryption

<img src="./assets/images/Asymmetric-encryption.png" alt="events" width="700" height="400">

* Asymmetrical encryption uses two separate keys for encryption and decryption. 
* These two keys are known as the **public key and the private key**. Together, both these keys form a **public-private key pair**.
* The public key, as the name suggest is openly distributed and shared with all parties. While it is closely linked with the private key.
* A message that is encrypted by a machine’s public key, can only be decrypted by the same machine’s private key.
* This one-way relation means that the public key cannot decrypt its own messages, nor can it decrypt anything encrypted by the private key.
* The private key must remain private i.e. for the connection to be secured, no third party must ever know it. 
* Asymmetrical encryption is not used to encrypt the entire SSH session. Instead, it is only used during the key exchange algorithm of symmetric encryption. 

### ✳Hashing

<img src="./assets/images/hashing.png" alt="events" width="700" height="400">

* **One-way hashing** is another form of cryptography used in Secure Shell Connections.
* It is easy to generate a cryptographic hash from a given input, but impossible to generate the input from the hash.
* This means that if a client holds the correct input, they can generate the crypto-graphic hash and compare its value to verify whether they possess the correct input.
* SSH uses hashes to verify the authenticity of messages. This is done using **HMACs, or Hash-based Message Authentication Codes**. 
* This ensures that the command received is not tampered with in any way.
* Each message that is transmitted must contain a **MAC**, which is calculated using the **symmetric key**, packet sequence number, and the message contents.

### ✳SSH with Encryption Techniques

<img src="./assets/images/ssh-client-and-server.jpg" alt="events" width="700" height="400">

* The way SSH works is by making use of a **client-server model to allow for authentication of two remote systems** and **encryption of the data that passes between them**.
* SSH operates on TCP port **22** by default (though this can be changed if needed). The host (server) listens on port 22 (or any other SSH assigned port) for incoming connections.
* The client must begin the SSH connection by initiating the **TCP handshake** with the server.
* There are two stages to establishing a connection: 
    * First both the systems must agree upon encryption standards to protect future communications.
    * Second, the user must authenticate themselves. If the credentials match, then the user is granted access.