Logs
====

- Part 7: Looking at logs
  - Commands: journalctl, less
  - Viewing logs with journalctl 
  - Viewing raw logs in /var/log/messages

Here are three exercises for each command (`journalctl`, viewing logs in the filesystem, and `dmesg`) to help you practice handling and analyzing system logs in Linux environments.

### Exercises for `journalctl` (Systemd Journal)
**Exercise 1: Viewing Logs for a Specific Service**
**Objective:** Learn to view logs for a specific systemd service using `journalctl`.
**Steps:**

1. Open your terminal.
2. Type `journalctl -u sshd` to view all journal entries for the SSH daemon.
3. Scroll through the entries to understand how the service has been performing or troubleshoot issues.

**Exercise 2: Viewing Logs Since the Last Boot**
**Objective:** Use `journalctl` to view all system logs since the last system boot.
**Steps:**

1. Type `journalctl -b` in your terminal.
2. Explore the log entries to see what activities and services were initiated at boot.

**Exercise 3: Filtering Logs by Priority**
**Objective:** Learn how to filter log entries by their priority level.
**Steps:**

1. Enter `journalctl -p err` to view all entries with the error priority.
2. Review the output to identify any critical errors that need attention.

### Exercises for Viewing Logs in the Filesystem
**Exercise 1: Viewing Apache Access Logs**
**Objective:** Learn to view and interpret Apache web server access logs.
**Steps:**

1. Navigate to the Apache log directory by typing `cd /var/log/apache2` or `/var/log/httpd` depending on your distribution.
2. Use `less access.log` to view access logs. Navigate through the file to see the requests handled by the server.

**Exercise 2: Monitoring Real-Time Log Updates**
**Objective:** Use `tail` to monitor real-time updates to a log file.
**Steps:**

1. Open a terminal and type `sudo tail -f /var/log/syslog` to follow the syslog file as it's updated.
2. Watch the live updates to the syslog, especially useful during troubleshooting or system changes.

**Exercise 3: Searching Logs with Grep**
**Objective:** Use `grep` to search through large log files for specific entries.
**Steps:**

1. In your log directory, use a command like `grep "error" /var/log/syslog` to find all occurrences of the word "error" in the syslog file.
2. Analyze the output to understand the context and frequency of errors logged.

### Exercises for `dmesg` (Display Message or Driver Message)
**Exercise 1: Viewing Hardware and Boot Messages**
**Objective:** Use `dmesg` to view kernel-related messages and hardware initialization during boot.
**Steps:**

1. Open a terminal and type `dmesg` to display the kernel ring buffer messages.
2. Browse through the messages to find details about hardware detection and initialization.

**Exercise 2: Filtering `dmesg` Output by Priority**
**Objective:** Filter the output of `dmesg` by a specific log level.
**Steps:**

1. Type `dmesg --level=err` to see all error messages from the kernel.
2. Review these messages to identify any potential issues with hardware or drivers.

**Exercise 3: Saving `dmesg` Output to a File**
**Objective:** Save the output of `dmesg` to a file for later analysis.
**Steps:**

1. Use the command `dmesg > dmesg_output.txt` to redirect the output to a file.
2. Open `dmesg_output.txt` with a text editor or `less` to review or share the file as needed.

