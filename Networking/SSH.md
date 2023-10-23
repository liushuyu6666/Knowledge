- [Overview](#overview)
- [Symmetric Cryptography and Asymmetric Cryptography](#symmetric-cryptography-and-asymmetric-cryptography)
- [Procedures](#procedures)
- [Practice](#practice)
  - [Client Preparation](#client-preparation)
  - [Server Preparation](#server-preparation)
  - [Double Check the Client and the Server:](#double-check-the-client-and-the-server)

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
To establish an SSH connection between the client and the server, follow these professional and concise instructions. Please note that the client will connect to the server using the "server_ssh" user, who has "sudo" privileges.

## Client Preparation
1. Generate an SSH key pair on the client machine:
    ```bash
    ssh-keygen -t <key_type>
    ```
    Replace `<key_type>` with "rsa," "ed25519," or "ecdsa."
2. By default, the key pair is saved in `~/.ssh/`. Take note of this location.
3. Ensure proper permissions on the SSH private key file on the client:
    ```bash
    chmod 600 </path/to/your/private_key>
    ```
## Server Preparation
1. Prepare the "server_ssh" user:
   1. Create the "server_ssh" user:
       ```bash
       sudo adduser server_ssh
       ```
   2. Grant "sudo" privileges:
      1. Open the `sudoers` file:
        ```bash
        sudo visudo
        ```
      2. Add the following line to the `sudoers` file:
        ```bash
        server_ssh ALL=(ALL:ALL) ALL
        ```
      3. Save the `sudoers` file.
      4. Add the user to the `sudo` group:
        ```bash
        sudo usermod -aG sudo server_ssh
        ```
   3. Test `sudo` privileges:
      1. Switch to the "server_ssh" user:
        ```bash
        su ubuntu_desktop
        ```
      2. Verify `sudo` privileges:
        ```bash
        sudo ls
        ```
      3. No password prompt should appear.
2. Configure `~/.ssh/authorized_keys` on the server from the client side:
   1. Typically, `~/.ssh/authorized_keys` on the server is empty. Please note that each user on a Unix-based system has their own home directory, and their `~/.ssh/authorized_keys` file is located in their respective home directory. For example, user "server_ssh" has a home directory at `/home/server_ssh`, and its `authorized_keys` file is located at `/home/server_ssh/.ssh/authorized_keys`.
   2. Copy the public key from the client to the server using:
    ```bash
    ssh-copy-id -i </path/to/your/public_key.pub> server_ssh@<server_ip>
    ```
   3. Connect to the server through SSH using a password from the client side:
    ```bash
    ssh server_ssh@<server_ip>
    ```
   4. Ensure correct permissions on `.ssh` and `authorized_keys` on the server:
    ```bash
    chmod 700 ~/.ssh
    chmod 600 ~/.ssh/authorized_keys
    ```
   5. Once `~/.ssh/authorized_keys` is successfully configured, you won't need a password for SSH connections. Use:
    ```bash
    ssh -i </path/to/your/public_key.pub> server_ssh@<server_ip>
    ```
## Double Check the Client and the Server:
To confirm that the configuration is complete:

1. Ensure that the IP address of the server is added to `~/.ssh/known_hosts` on the client. This should be done automatically the first time the client tries to connect to the server.
2. Confirm that the public key is added to `~/.ssh/authorized_keys` on the server.
