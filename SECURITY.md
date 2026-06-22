# Security Policy

## Supported Versions

This project is actively maintained on the `master` branch. Security fixes are applied to the latest version only.

| Version | Supported |
| ------- | --------- |
| latest (`master`) | :white_check_mark: |
| older commits | :x: |

## Reporting a Vulnerability

If you discover a security vulnerability, please report it privately:

- Use GitHub's [private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability) ("Report a vulnerability" under the **Security** tab), **or**
- Email the maintainer at **nipon@6amtech.com**.

Please include steps to reproduce, affected versions, and potential impact. You can expect an initial response within **5 business days**. Please do not open a public issue for security reports.

## Security Considerations

- This script must be run as **root** and installs system packages with `apt`. Review the script before running it, and only run it on a server you own or are authorized to administer.
- The script runs `mysql_secure_installation`, which is interactive: set a strong MySQL root password and accept the prompts to remove anonymous users, disallow remote root login, and drop the test database.
- The script does not configure a firewall, TLS/HTTPS, or virtual hosts. After installation, harden Apache/PHP, enable a firewall (e.g. `ufw`), and configure TLS before exposing the server to the internet.
