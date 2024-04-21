Secure remote access
====================

- Part 4: Secure remote access
  - Commands: ssh, ssh-keygen, ssh-copy-id, ssh-add, ssh-agent
  - Files: $HOME/.ssh/authorized_keys
  - Using Secure Shell (SSH)
  - Generating keys, copying keys, adding keys to ssh-agent 

## Introduction to SSH in Linux

Secure Shell (SSH) is a cryptographic network protocol used for secure communication between a client and a server over an unsecured network. SSH is widely used for managing systems and applications remotely, allowing secure file transfer, command execution, and network services. SSH uses a pair of cryptographic keys to authenticate sessions and encrypt data, significantly enhancing security.

### Basic Concept of Public and Private Keys

SSH operates using a pair of keys:
- **Public Key:** Can be shared with anyone and is used to encrypt messages that only the private key can decrypt.
- **Private Key:** Must be kept secure and is used to decrypt messages that were encrypted with the public key.

This system ensures that even if the public key is intercepted, without the corresponding private key, no meaningful information can be decrypted.

## Generating SSH Keys

### Steps to Generate RSA and ED25519 Keys

Generating SSH keys on Linux can be done using the `ssh-keygen` command. The two most recommended types of keys are RSA and ED25519, with ED25519 being favored for its security and performance:

1. **Generate an RSA Key:**
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
   This command creates a new RSA key with a 4096-bit length, providing a good balance between compatibility and security.

2. **Generate an ED25519 Key:**
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```
   ED25519 is known for its efficiency at short key lengths, offering better performance with comparable security.

### Best Practices for Key Generation

- **Secure Passphrase:** Always use a strong, unique passphrase for your SSH keys to add an additional layer of security.
- **Regular Updates:** Regularly update your SSH keys to mitigate the risk of key compromise.

## Copying SSH Keys to Remote Hosts

### Using `ssh-copy-id` for Simplicity

The easiest way to copy your public key to a remote server is using the `ssh-copy-id` command:
   ```bash
   ssh-copy-id -i ~/.ssh/mykey.pub user@hostname
   ```
This command appends the public key in `mykey.pub` to the remote host's `~/.ssh/authorized_keys` file, enabling passwordless login.

### Manual Method of Copying Keys

If `ssh-copy-id` is not available, you can manually copy the key by:
1. Copying the public key content:
   ```bash
   cat ~/.ssh/mykey.pub
   ```
2. Logging into the remote server and appending this content to `~/.ssh/authorized_keys`:
   ```bash
   echo your_public_key_string >> ~/.ssh/authorized_keys
   ```

Continuing from where we left off, we'll now delve into the functionalities and configurations of the `ssh-agent`, followed by an in-depth look at key SSH configuration files.

## Adding Keys to `ssh-agent`

### What is `ssh-agent`?

`ssh-agent` is a background program that handles private keys used for public key authentication, eliminating the need to enter a passphrase each time it is used. It is particularly useful for managing multiple keys or when using automated scripts that rely on SSH.

### How to Add Keys to the Agent

To use `ssh-agent` for managing your SSH keys, you need to start the agent and add your keys to it:

1. **Starting `ssh-agent`:**
   ```bash
   eval $(ssh-agent -s)
   ```
   This command starts the agent and sets the necessary environment variables.

2. **Adding SSH Keys:**
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```
   Replace `id_ed25519` with your private key file. If prompted, enter your passphrase.

## Configuring the SSH Agent

### Automation of `ssh-agent` Startup

Automating the startup of `ssh-agent` ensures that the agent is running whenever you start a new session. This can be done by adding the `ssh-agent` startup command to your shell's initialization script, such as `~/.bash_profile` or `~/.bashrc`:

```bash
if [ -z "$SSH_AUTH_SOCK" ] ; then
  eval $(ssh-agent -s)
  ssh-add
fi
```

This script checks if `ssh-agent` is already running; if not, it starts the agent and adds the keys.

### Managing Multiple Keys with the Agent

When working with multiple keys, you might want to specify which keys `ssh-agent` should use, especially to avoid reaching the maximum number of authentication attempts allowed by servers:

```bash
ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/id_ed25519
```

Use `ssh-add -l` to list all keys currently managed by the agent, and `ssh-add -D` to clear all keys from the agent when needed.

## Understanding Key Files and Directories

### Role of `$HOME/.ssh/authorized_keys`

The `authorized_keys` file within the `$HOME/.ssh` directory plays a crucial role in SSH authentication. It stores all the public keys that are allowed to access the server. Each line in this file represents one public key, and you can add keys manually or using `ssh-copy-id`.

### Configuring and Using `$HOME/.ssh/config`

The `config` file in the `$HOME/.ssh` directory allows users to create aliases for hostnames and specify settings for individual hosts, making it easier to manage connections to multiple servers. Here’s how you can configure it:

```bash
Host myserver
    HostName server.example.com
    User myusername
    IdentityFile ~/.ssh/myserver_rsa
    Port 2222
```

This configuration:
- **Alias `myserver` for `server.example.com`**
- **Sets `myusername` as the default username**
- **Uses a specific private key**
- **Connects to port 2222 instead of the default SSH port 22**

## Exercises

### Exercise Set for `ssh` (Secure Shell)
**Exercise 1:** Connect to a Remote Server

1. If you have access to a remote server (make sure you have permission to access it), open your terminal.
2. Connect using `ssh username@hostname` (replace `username` with your actual username on the server and `hostname` with the server's IP address or domain name).
3. If connected successfully, execute a simple command like `ls` or `pwd` to ensure the connection is working.

**Exercise 2:** Running a Command on a Remote Server
1. Without logging into the server's interactive shell, run a command remotely: `ssh username@hostname pwd`.
2. This command should output the current working directory on the remote server.

### Exercise Set for `ssh-keygen` (SSH Key Generator)
**Exercise 1:** Generate a New SSH Key Pair

1. In your terminal, type `ssh-keygen -t rsa -b 4096` to generate a new RSA key pair with 4096 bits.
2. Follow the prompts to choose the file in which to save the key and enter a passphrase for added security.

**Exercise 2:** View and Confirm the SSH Key Pair

1. Navigate to the directory where the keys are stored (usually `~/.ssh/`).
2. Use `cat ~/.ssh/id_rsa.pub` to view the public key.

### Exercise Set for `ssh-copy-id` (Copy SSH Key to Remote Server)
**Exercise 1:** Copy Your SSH Public Key to a Server

1. Assuming you have a remote server where you have password-based SSH access, type `ssh-copy-id username@hostname`.
2. Enter your password when prompted to copy your public key to the server's authorized keys.

**Exercise 2:** SSH into the Server Without a Password

1. After copying the key, try to SSH into the server again using `ssh username@hostname`.
2. If the key was successfully copied, you should not be prompted for a password.

### Exercise Set for `ssh-add` (Add SSH Key to the Agent)
**Exercise 1:** Add SSH Key to the SSH Agent

1. First, ensure the ssh-agent is running: `eval "$(ssh-agent -s)"`.
2. Add your SSH private key to the agent using `ssh-add ~/.ssh/id_rsa`.
3. Enter your passphrase if prompted.

**Exercise 2:** List the Keys Added to the Agent

1. Check which keys are loaded into the ssh-agent by typing `ssh-add -l`.
2. The output will list all keys currently managed by the agent.

### Exercise Set for `ssh-agent` (SSH Authentication Agent)
**Exercise 1:** Start the SSH Agent

1. Open your terminal and start the ssh-agent with `eval "$(ssh-agent -s)"`.
2. Note the agent PID that is output to the terminal.

**Exercise 2:** Use the SSH Agent with SSH-Add

1. After starting the ssh-agent, add a key as done in the previous exercise.
2. SSH into a server to verify that the agent is using the key for authentication without needing to re-enter the passphrase.
