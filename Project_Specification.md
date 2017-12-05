# Project Specification

## User Management
Criteria | Meets Specifications
---------|----------------------
Can you log into the server as the user `grader` using the submitted key? | The SSH key submitted with the project can be used to log in as `grader` on the server
Is remote login of the `root` user disabled? | You cannot log in as `root` remotely.
Is the `grader` user given `sudo` access? | The `grader` user can run commands using `sudo` to inspect files that are readable only by root.

## Security
Criteria | Meets Specification
---------|---------------------
Is the firewall configured to only allow for `SSH`, `HTTP`, and `NTP`? | Only allow connections for `SSH` (port 2200), `HTTP` (port 80), and `NTP` (port 123).
Are users required to authenticate using `RSA` keys? | Key-based `SSH` authentication is enforced.
Are the applications up-to-date? | All system packages have been updated to most recent versions.
Is `SSH` hosted on non-default port? | `SSH` is hosted on non-default port.













