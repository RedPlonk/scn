Firewalls and Security
======================

- Part 8: Firewalls, firewall maintenance, and security
  - Commands: iptables, ufw, selinux, apparmor, aide
  - Listing, adding, and removing firewall rules
  - Viewing firewall logs

These exercises will help you understand and practice basic commands and configurations for Linux security tools, including iptables, ufw, SELinux, AppArmor, and AIDE.

### Exercises for `iptables` (Network Packet Filter)
**Exercise 1: Listing Current iptables Rules**
**Objective:** Learn to display all current iptables rules.
**Steps:**

1. Open a terminal and type `sudo iptables -L`.
2. Observe the output, noting how rules are organized into chains (INPUT, FORWARD, OUTPUT).

**Exercise 2: Blocking an IP Address**
**Objective:** Use iptables to block all traffic from a specific IP address.
**Steps:**

1. To block incoming traffic from IP address 192.168.1.100, type `sudo iptables -A INPUT -s 192.168.1.100 -j DROP`.
2. Verify that the rule has been added by checking the rules list again with `sudo iptables -L`.

**Exercise 3: Allowing Port Access**
**Objective:** Configure iptables to allow access to a specific port (e.g., port 80 for web traffic).
**Steps:**

1. Allow traffic on port 80 by typing `sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT`.
2. Verify the rule by listing the iptables rules.

### Exercises for `ufw` (Uncomplicated Firewall)
**Exercise 1: Enabling and Checking Status**
**Objective:** Enable ufw and check its status.
**Steps:**

1. Enable ufw by typing `sudo ufw enable`.
2. Check the status with `sudo ufw status verbose` to see which rules are active.

**Exercise 2: Adding Firewall Rules**
**Objective:** Add rules to allow traffic on common ports.
**Steps:**

1. Allow SSH traffic by typing `sudo ufw allow 22/tcp`.
2. Allow HTTP web traffic by typing `sudo ufw allow 80/tcp`.
3. List all active rules with `sudo ufw status`.

**Exercise 3: Denying Traffic to a Port**
**Objective:** Learn to deny traffic to a specific port.
**Steps:**

1. Deny access to port 21 (FTP) by typing `sudo ufw deny 21/tcp`.
2. Verify the rule by checking the firewall status.

### Exercises for `SELinux` (Security-Enhanced Linux)
**Exercise 1: Checking SELinux Status**
**Objective:** Determine the current mode of SELinux.
**Steps:**

1. Check the SELinux status by typing `sestatus`.
2. Note whether SELinux is enabled and whether it is in enforcing, permissive, or disabled mode.

**Exercise 2: Changing SELinux Mode**
**Objective:** Temporarily change the SELinux mode.
**Steps:**

1. Set SELinux to permissive mode by typing `sudo setenforce 0`.
2. Verify the change with `sestatus`.

**Exercise 3: Restoring File Contexts**
**Objective:** Use `restorecon` to restore the correct SELinux context on a file.
**Steps:**

1. Create a new file with `touch /var/www/html/index.html`.
2. Restore default SELinux context by typing `restorecon /var/www/html/index.html`.
3. Check the context with `ls -Z /var/www/html/index.html`.

### Exercises for `AppArmor` (Application Security)
**Exercise 1: Listing AppArmor Profiles**
**Objective:** View all AppArmor profiles and their status.
**Steps:**

1. List all profiles by typing `sudo aa-status`.
2. Note which applications are protected and their enforcement modes (enforcing or complain).

**Exercise 2: Changing Profile Mode**
**Objective:** Change an AppArmor profile mode from enforcing to complain.
**Steps:**

1. Switch the profile mode for a specific application, e.g., `sudo aa-complain /usr/sbin/nginx`.
2. Verify the change by listing the profiles again.

**Exercise 3: Reload an AppArmor Profile**
**Objective:** Learn how to reload a profile after making changes.
**Steps:**

1. Modify an AppArmor profile using your favorite editor.
2. Reload the profile with `sudo apparmor_parser -r /etc/apparmor.d/profile.name`.

### Exercises for `AIDE` (Advanced Intrusion Detection Environment)
**Exercise 1: Initializing AIDE Database**
**Objective:** Create the initial AIDE database.
**Steps:**

1. Initialize the AIDE database with `sudo aide --init`.
2. Confirm that a new database file has been created in the `/var/lib/aide` directory.

**Exercise 2: Checking the System Integrity**
**Objective:** Use AIDE to check for changes in the system.
**Steps:**

1. After initialization, make a change to a file tracked by AIDE, like modifying `/etc/passwd`.
2. Run `sudo aide --check` to see if

 AIDE detects the modification.

**Exercise 3: Updating the AIDE Database**
**Objective:** Update the AIDE database after making authorized changes.
**Steps:**

1. After making legitimate changes and verifying them, update the database with `sudo aide --update`.
2. Rename the new database to become the primary database using `sudo mv /var/lib/aide/aide.db.new.gz /var/lib/aide/aide.db.gz`.
