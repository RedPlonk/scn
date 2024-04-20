Secure remote access
====================

- Part 4: Secure remote access
  - Commands: ssh, ssh-keygen, ssh-copy-id, ssh-add, ssh-agent
  - Files: $HOME/.ssh/authorized_keys
  - Using Secure Shell (SSH)
  - Generating keys, copying keys, adding keys to ssh-agent 

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
