Package Management

This section covers Linux package management using APT and DPKG, including installing, removing, updating, searching, and inspecting packages.

Overview

Linux distributions use package managers to install and manage software.

On Debian-based systems, two important package management tools are:

· apt
· dpkg

apt provides a higher-level interface for package management, while dpkg works directly with Debian package files.

---

APT

APT is used to manage software packages and their dependencies on Debian-based systems.

The general syntax is:

```bash
apt [command] [package]
```

---

Updating Package Information

Use apt update to update the local package information.

```bash
sudo apt update
```

This refreshes the information about available packages from configured repositories.

---

Upgrading Packages

Use apt upgrade to upgrade installed packages.

```bash
sudo apt upgrade
```

A combination of update and upgrade is commonly used:

```bash
sudo apt update
sudo apt upgrade
```

---

Installing Packages

Use apt install to install a package.

```bash
sudo apt install package-name
```

Example:

```bash
sudo apt install curl
```

APT resolves and installs required dependencies.

---

Removing Packages

Use apt remove to remove an installed package.

```bash
sudo apt remove package-name
```

Example:

```bash
sudo apt remove curl
```

---

Removing Packages and Configuration Files

purge can be used when removing a package and its associated configuration files.

```bash
sudo apt purge package-name
```

Example:

```bash
sudo apt purge curl
```

---

Searching for Packages

Use apt search to search for available packages.

```bash
apt search keyword
```

Example:

```bash
apt search nginx
```

---

Showing Package Information

Use apt show to display information about a package.

```bash
apt show package-name
```

Example:

```bash
apt show curl
```

The output can include information such as:

· Package name
· Version
· Description
· Dependencies
· Package size

---

Listing Installed Packages

dpkg can be used to list installed packages.

```bash
dpkg -l
```

To search the installed package list:

```bash
dpkg -l | grep package-name
```

Example:

```bash
dpkg -l | grep curl
```

---

DPKG

Overview

dpkg is the lower-level package management system used by Debian-based distributions.

It works directly with .deb packages.

---

Installing a .deb Package

Use dpkg -i to install a local Debian package.

```bash
sudo dpkg -i package.deb
```

Example:

```bash
sudo dpkg -i example.deb
```

---

Removing a Package with DPKG

Use:

```bash
sudo dpkg -r package-name
```

Example:

```bash
sudo dpkg -r curl
```

---

Listing Package Information

To list installed packages:

```bash
dpkg -l
```

---

Finding Files Installed by a Package

Use:

```bash
dpkg -L package-name
```

Example:

```bash
dpkg -L curl
```

This displays files installed by the package.

---

Checking Which Package Owns a File

Use:

```bash
dpkg -S /path/to/file
```

Example:

```bash
dpkg -S /usr/bin/curl
```

This can identify the installed package that provides a specific file.

---

APT vs DPKG

APT and DPKG serve different roles.

Tool Purpose
apt High-level package management
dpkg Low-level Debian package management

APT handles repositories and dependencies, while DPKG directly manages Debian packages.

---

Package Management Workflow

A common workflow is:

1. Update Package Information

```bash
sudo apt update
```

2. Search for a Package

```bash
apt search package-name
```

3. Check Package Information

```bash
apt show package-name
```

4. Install the Package

```bash
sudo apt install package-name
```

5. Check Installed Packages

```bash
dpkg -l | grep package-name
```

6. Remove the Package

```bash
sudo apt remove package-name
```

---

Practical Examples

Update Package Information

```bash
sudo apt update
```

Upgrade Installed Packages

```bash
sudo apt upgrade
```

Search for a Package

```bash
apt search nginx
```

Display Package Information

```bash
apt show nginx
```

Install a Package

```bash
sudo apt install nginx
```

Remove a Package

```bash
sudo apt remove nginx
```

Purge a Package

```bash
sudo apt purge nginx
```

List Installed Packages

```bash
dpkg -l
```

Search Installed Packages

```bash
dpkg -l | grep nginx
```

Install a Local .deb Package

```bash
sudo dpkg -i package.deb
```

List Files Installed by a Package

```bash
dpkg -L nginx
```

Find Which Package Owns a File

```bash
dpkg -S /usr/bin/curl
```

---

Useful Commands

Command Purpose
apt update Update package information
apt upgrade Upgrade installed packages
apt install Install a package
apt remove Remove a package
apt purge Remove a package and its configuration files
apt search Search for packages
apt show Display package information
dpkg -l List installed packages
dpkg -i Install a .deb package
dpkg -r Remove a package
dpkg -L List files installed by a package
dpkg -S Find which package provides a file

---

Key Takeaways

· APT and DPKG are package management tools used on Debian-based Linux systems.
· APT provides higher-level package management and handles repositories and dependencies.
· DPKG directly manages Debian packages.
· apt update refreshes package information.
· apt upgrade upgrades installed packages.
· apt install installs packages.
· apt remove removes packages.
· apt purge removes packages and their configuration files.
· apt search searches available packages.
· apt show displays package information.
· dpkg -l lists installed packages.
· dpkg -i installs local .deb packages.
