Network Services
================

- Part 6: Network services
  - Commands: systemctl
  - Enabling, starting, and stopping network services
  - Verifying connectivity. 

`systemctl` is a utility in Linux systems that is part of the systemd system and service manager. It is used to examine and control the systemd system and service manager. Here are five practical exercises designed to help you learn to manage services and system resources using `systemctl`.

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

