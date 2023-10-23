- [Overview](#overview)
- [Symmetric Cryptography and Asymmetric Cryptography](#symmetric-cryptography-and-asymmetric-cryptography)
- [Procedures](#procedures)
- [Practice](#practice)

# Overview
In practice, SSH communication involves two primary methods: key-based authentication and password-based authentication.

The SSH communication can be broken down into two key components - Asymmetric Cryptography (Public Key Authentication) and Symmetric Cryptography (Session Keys).

Assuming this scenario where the client machine tries to connect to a remote server.

# Symmetric Cryptography and Asymmetric Cryptography
Symmetric cryptography employs a single shared secret key that serves both encryption and decryption functions. In contrast, asymmetric cryptography operates with a key pair: a public key and a private key. The public key is used for encryption, and anyone can have access to it. It is typically used to send encrypted messages or verify digital signatures. The private key is kept secret and is used for decryption and signing. Only the owner of the private key should have access to it.

# Procedures
1. Key Pair Generation
   1. On the client machine, generate a public and private key pair.
      * Use the `ssh-keygen` command to generate the key pair.
   2. Add the client's public key to the authorized keys list on the target server.
      * Use the `ssh-copy-id` command to copy the public key, or
      * Manually add the public key.
   3. When connect to an SSH server for the first time using a command like "ssh <server_name>@<ip_address>", the client will display a message similar to the following:
    ```txt
    The authenticity of host 'hostname (IP address)' can't be established.
    ECDSA key fingerprint is SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.
    Are you sure you want to continue connecting (yes/no)?
    ```
    By typing "yes", the server's key is added to the `known_hosts`.
2. Client Authentication (Asymmetric Cryptography)
   1. When the client connects to the remote server, it offers its public key.
   2. The server checks whether the client's public key is in its list of authorized keys.
   3. If the public key is authorized, the server sends a challenge (encrypted message) to the client.
3. Server Authentication (Asymmetric Cryptography)
   1. The client decrypts the server's challenge using its private key and signs it.
   2. The client sends the signed response back to the server.
   3. The server verifies the signature using the stored public key, since only the matching private key can decrypt the challenge and sign it, the server authenticate the client and grant the access.
4. Secure Channel Establishment (Symmetric Cryptography)
   1. Once the server and client have authenticated each other, two session keys are generated independently by both the client and server, based on a combination of the client's and server's public keys, along with random data.
   2. Then the client and the server will exchange their session keys.
   3. These session keys are used to encrypt and decrypt data for secure communication, including commands such as "sudo apt upgrade".

# Practice
In the context of a scenario where the client establishes an SSH connection with the server, you can find the detailed operational steps outlined [here](https://github.com/liushuyu6666/Learn_Ansible/blob/master/readme.md#raspberry-pi-setup-guide). During this process, consider the Raspberry Pi as the equivalent of the server and the MacBook as the client.

All the actions described above correspond to Step 1 in the procedure section. Steps 2 and 3 will be executed automatically behind the screen.

