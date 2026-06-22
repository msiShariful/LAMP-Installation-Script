# LAMP Installation Script

> Interactive Bash script to install and configure a LAMP stack (Apache, MySQL, PHP) on Debian/Ubuntu in one run.

![Bash](https://img.shields.io/badge/Bash-4EAA25?logo=gnubash&logoColor=white)
![Apache](https://img.shields.io/badge/Apache-D22128?logo=apache&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?logo=php&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Ubuntu%20%2F%20Debian-E95420?logo=ubuntu&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

A single Bash script that installs and configures a complete LAMP stack (Linux, Apache, MySQL, PHP) on a Debian/Ubuntu system. Run it once and you get a working Apache web server, MySQL database server, and PHP runtime, with a guided MySQL hardening step.

## What it does

The script performs the following steps in order:

1. **Requires root.** It checks for superuser privileges and exits with a message asking you to run it with `sudo` if it is not run as root.
2. **Updates package lists and installs the stack.** It runs `apt update`, then `apt install -y apache2 mysql-server php libapache2-mod-php php-mysql`.
3. **Hardens MySQL.** It runs `mysql_secure_installation`, the interactive MySQL security setup.
4. **Enables Apache rewrite and restarts Apache.** It runs `a2enmod rewrite` to enable the rewrite module, then `systemctl restart apache2`.

## Requirements

- A Debian/Ubuntu system with the `apt` package manager.
- `sudo`/root access.
- An active internet connection (to download packages).

## Usage

```bash
git clone https://github.com/msiShariful/LAMP-Installation-Script.git
cd LAMP-Installation-Script
chmod +x install_lamp.sh
sudo ./install_lamp.sh
```

> **Note:** The script is interactive. The `mysql_secure_installation` step will prompt you for the MySQL root password and a series of hardening choices (removing anonymous users, disallowing remote root login, dropping the test database, and so on). Answer the prompts to complete the install.

## Verify the install

After the script finishes, confirm each component is installed:

```bash
apache2 -v
mysql --version
php -v
```

Then open a browser and visit [http://localhost](http://localhost) — you should see the Apache default welcome page.

## Notes / Compatibility

- This script uses `apt`, so it works only on the **Debian/Ubuntu** family of distributions.
- It is **not** compatible with RHEL/CentOS/Fedora (which use `yum`/`dnf`) or other non-`apt` systems.
- It does not configure SSL/TLS, virtual hosts, or a firewall — it installs and starts the core stack only.

## Security

This script must be run as **root** and installs system packages. Review the script before running it, and only run it on a server you own or are authorized to administer. See [SECURITY.md](SECURITY.md) for the full security policy and considerations.

## Contributing

Contributions are welcome. Feel free to open an issue or submit a pull request with improvements, bug fixes, or compatibility enhancements.

## License

This project is licensed under the [MIT License](LICENSE).
