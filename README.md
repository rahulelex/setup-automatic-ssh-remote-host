# Setup automatic SSH login in ubuntu
Typically this involves using SSH key pairs, which allow you to securely authenticate to remote servers without entering a password every time. Here's a step-by-step guide on how to set it up:

Note: This guide assumes you're using a Unix-like operating system (e.g., Linux or macOS). If you're using Windows, you can use tools like PuTTY or Windows Subsystem for Linux (WSL) to achieve similar functionality.

### Step 1: Generate SSH Key Pair:
> You can skip this step If you already have ssh key pair in id_rsa.pub file.

If you don't already have an SSH key pair, you can generate one using the following command:
```sh
ssh-keygen -t rsa -b 4096
```
This command will create a 4096-bit RSA key pair by default. You can change the -b option to specify a different key size if needed.

### Step 2: Copy the Public Key to the Remote Server:
Use the ssh-copy-id command to copy your public key to the remote server. Replace user and hostname with your remote server's username and IP address or domain name:
```sh
ssh-copy-id user@hostname
```
This command will prompt you for the remote user's password. Once you enter it, your public key will be added to the ~/.ssh/authorized_keys file on the remote server, allowing you to log in without a password.

### Step 3: Test SSH Authentication:
To ensure that automatic SSH login is working, try to SSH into the remote server:
```sh
ssh user@hostname
```
##### You should now be able to log in without being prompted for a password.

Optional: Configure SSH Config File (Optional but recommended):
### Step 4: To simplyfy your SSH connection
You can create or modify your SSH config file (~/.ssh/config) to simplify your SSH connections. Here's an example:

```sh
Host myserver
    HostName hostname
    User user
    IdentityFile ~/.ssh/id_rsa
```
> Make sure to replace <myserver> with the word you want to ssh , <hostname> with your remote hostname's IP address and <user> with your remote username

### Step 5: After adding this configuration, you can SSH into the server using:
```sh
ssh myserver
```
This saves you from specifying the username, hostname, and identity file each time you connect.

> Secure Your Private Key:
Make sure your private key (~/.ssh/id_rsa by default) is kept secure. Only you should have access to it, and it should be protected with proper file permissions.
Now, you have set up automatic SSH login using SSH key pairs. You can use this method to securely connect to remote servers without needing to enter a password each time you SSH into them.
