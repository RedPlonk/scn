Network Services
================

- Part 6: Network services
  - Commands: systemctl
  - Enabling, starting, and stopping network services
  - Verifying connectivity. 

Expanding on the initial descriptions of the top five essential Linux network services, let's delve deeper into the installation, maintenance, and configuration aspects of each service, as well as discuss some of the popular versions or implementations of these services.

### SSH (Secure Shell)

#### Installation
SSH is typically pre-installed on most Linux distributions. For distributions where it is not pre-installed, you can easily install it using the package manager. For example, on Debian-based systems (like Ubuntu):
```bash
sudo apt install openssh-server
```
And on Red Hat-based systems:
```bash
sudo yum install openssh-server
```

#### Maintenance and Configuration
Configuration of SSH is handled through the `/etc/ssh/sshd_config` file. Key settings to consider adjusting include `PermitRootLogin` (to disable root logins for security) and `PasswordAuthentication` (to disable password logins in favor of key-based authentication). Restart the SSH service to apply changes:
```bash
sudo systemctl restart sshd
```

Regular updates and security patches are vital for maintaining SSH security, especially to mitigate vulnerabilities in older versions.

#### Popular Versions
- **OpenSSH**: The most widely used SSH implementation, known for its robust security features.
- **Dropbear SSH**: A lightweight alternative, useful for memory-constrained environments.

### HTTP/HTTPS (Web Services)

#### Installation
Web servers like Apache and Nginx are easily installed via package managers. For Apache on Ubuntu:
```bash
sudo apt install apache2
```
For Nginx on Ubuntu:
```bash
sudo apt install nginx
```

#### Maintenance and Configuration
For Apache, configurations are handled in `/etc/apache2/apache2.conf` and individual site configurations within `/etc/apache2/sites-available/`. For Nginx, configurations are typically in `/etc/nginx/nginx.conf` and `/etc/nginx/sites-available/`.

Ensure to regularly update your web server software to keep up with security patches. For HTTPS, use Let’s Encrypt for free SSL certificates, configuring automatic renewal to maintain SSL validity.

#### Popular Versions
- **Apache HTTP Server**: Known for its flexibility and power.
- **Nginx**: Renowned for its efficiency and low resource consumption.
- **LiteSpeed**: Commercial software known for high performance and scalability.

### FTP (File Transfer Protocol)

#### Installation
Install FTP servers like vsftpd (very secure FTP daemon) or ProFTPd using the package manager:
```bash
sudo apt install vsftpd
```
Or:
```bash
sudo yum install vsftpd
```

#### Maintenance and Configuration
FTP server configuration is managed via `/etc/vsftpd.conf` for vsftpd. Important settings to adjust include `anonymous_enable` (to disable anonymous logins) and `local_enable` (to allow local users to log in). Use `ftp_ssl_enable` to add a layer of security with SSL/TLS.

Regular monitoring of FTP logs in `/var/log/vsftpd.log` helps maintain security and operational integrity.

#### Popular Versions
- **vsftpd**: Known for security and speed.
- **ProFTPd**: Offers extensive configurability.

### DNS (Domain Name System)

#### Installation
Install BIND (Berkeley Internet Name Domain), a popular DNS software, via:
```bash
sudo apt install bind9
```
Or:
```bash
sudo yum install bind
```

#### Maintenance and Configuration
Configure DNS settings in `/etc/bind/named.conf` and zone files in `/etc/bind/zones/`. It's crucial to keep your DNS server up-to-date to protect against DNS spoofing and cache poisoning.

#### Popular Versions
- **BIND**: The most widely used DNS software.
- **PowerDNS**: Features a built-in web interface and API support.

### DHCP (Dynamic Host Configuration Protocol)

#### Installation
Install DHCP server software such as ISC DHCP server:
```bash
sudo apt install isc-dhcp-server
```
Or:
```bash
sudo yum install dhcp
```

#### Maintenance and Configuration
DHCP configuration is managed via `/etc/dhcp/dhcpd.conf`. Key parameters include defining subnets, ranges of IP addresses to be assigned, and lease times. Consistent monitoring and auditing of DHCP logs (`/var/log/syslog` or `/var/log/dhcpd.log`) are essential for ensuring that IP address management is functioning correctly.

#### Popular Versions
- **ISC DHCP Server**: Extensively used with robust features.
- **Dnsmasq**: Lightweight, also provides DNS caching capabilities.

Each of these services plays a critical role in network management and has its specific considerations for installation, configuration, and maintenance. Ensuring these services are securely configured and regularly updated is paramount to maintaining a reliable and secure network infrastructure.

## Exercises

### Exercise 1: Checking the Status of a Service
**Objective:** Learn how to check the status of a service using `systemctl`.

**Steps:**

1. Open your terminal.
2. Type `sudo systemctl status sshd` to check the status of the SSH server service on your machine.
3. Observe the output, which includes whether the service is active, its start time, and its recent logs.

### Exercise 2: Starting and Stopping Services
**Objective:** Learn how to start and stop services.

**Steps:**

1. To stop a service (for example, the Apache server), type `sudo systemctl stop apache2`.
2. Check if the service has stopped by using `sudo systemctl status apache2`.
3. Start the service again with `sudo systemctl start apache2`.
4. Verify that the service is running again by checking its status.

### Exercise 3: Enabling and Disabling Services
**Objective:** Learn how to enable and disable services to start automatically at boot.

**Steps:**

1. Disable a service (for example, the Bluetooth service) so it does not start at boot using `sudo systemctl disable bluetooth`.
2. Check if the service is disabled from starting at boot using `sudo systemctl is-enabled bluetooth`.
3. Enable the service again with `sudo systemctl enable bluetooth`.
4. Verify that the service is enabled to start at boot by checking its status with `sudo systemctl is-enabled bluetooth`.

### Exercise 4: Listing Active Services
**Objective:** Learn how to list all currently active services.

**Steps:**

1. Type `sudo systemctl list-units --type=service --state=running` to display a list of all active services.
2. Observe the output and try to identify some of the key services running on your system (e.g., network manager, web server).

### Exercise 5: Masking and Unmasking Services
**Objective:** Learn how to prevent a service from being started manually or automatically.

**Steps:**

1. Mask a service (e.g., the `cups` service for printing) by typing `sudo systemctl mask cups`.
2. Try to start the service using `sudo systemctl start cups`. Note that the service should not start because it is masked.
3. Check the status using `sudo systemctl status cups` to confirm it has not started and is indeed masked.
4. Unmask the service with `sudo systemctl unmask cups` to allow it to be started again.
5. Start the service to ensure it can now run after unmasking.

