# Phone Directory Application - Installation Instructions

This repository contains the Phone Directory Application, which allows users to manage and search for contact information efficiently. This document provides step-by-step instructions to set up the application on a Raspberry Pi using SQL and MariaDB.

## Table of Contents
1. [Setting Up Raspberry Pi, SQL, and MariaDB](#setting-up-raspberry-pi-sql-and-mariadb)
    - [1.1 Physical Setup of Raspberry Pi](#11-physical-setup-of-raspberry-pi)
    - [1.2 Installing Raspberry Pi Imager](#12-installing-raspberry-pi-imager)
    - [1.3 Installing Ubuntu on the SD Card](#13-installing-ubuntu-on-the-sd-card)
    - [1.4 Setting up the OS (Ubuntu) on Raspberry Pi](#14-setting-up-the-os-linux-on-raspberry-pi)
    - [1.5 Command Line Setup](#15-command-line-setup)
    - [1.6 Creating a Database User in MariaDB](#16-creating-a-database-user-in-mariadb)

---

## 1. Setting Up Raspberry Pi, SQL, and MariaDB

### 1.1 Physical Setup of Raspberry Pi
- Follow this [video guide](https://youtu.be/S9CYlpbSz-c?si=zw-Jelt5Yc_EjZT9) to physically set up your Raspberry Pi, including connecting the power, monitor, and peripherals.

### 1.2 Installing Raspberry Pi Imager
1. Visit the [Raspberry Pi Software](https://www.raspberrypi.com/software/).
2. Scroll down to "Download for Windows/macOS/Ubuntu" and choose your operating system.
3. Download the appropriate installer and run it.
4. If prompted, click **Yes** to allow changes, then click **Install**.
5. Once installed, check the "Run Raspberry Pi Imager" box and click **Finish**.

### 1.3 Installing Ubuntu on the SD Card
1. Power off your Raspberry Pi and remove the SD card.
2. Insert the SD card into your computer.
3. Open the Raspberry Pi Imager.
4. Select **Choose OS**, scroll to **Other general-purpose OS**, and choose **Ubuntu Desktop 24.04.1 LTS (64-bit)**.
5. Select **Choose Storage** and pick the SD card.
6. Click **Next** and follow the instructions to install Ubuntu onto the SD card.
7. Once done, reinsert the SD card into the Raspberry Pi and power it on.

### 1.4 Setting up the OS (Linux) on Raspberry Pi
1. Select your language and keyboard layout.
2. Connect to your network and set your Wi-Fi password.
3. Set the timezone, name, and create a user account with a secure password.
4. Let the system install (don’t click **Skip**).
5. Skip Ubuntu Pro registration for now.

### 1.5 Command Line Setup
After setting up Ubuntu, open the terminal and run these commands to update and prepare your system:

#### Update the system:
```bash
sudo apt update
sudo apt upgrade
```

#### Set up the firewall:
```bash
sudo apt install ufw
sudo ufw enable
sudo ufw allow ssh
sudo ufw status
```

#### Enable SSH:
```bash
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh
```

#### Install Git, Python, and MariaDB:
```bash
sudo apt install python3-pip git mariadb-server
```

### 1.6 Creating a Database User in MariaDB
1. Log in to MariaDB as root:
```bash
sudo mariadb -u root
```
2. Create a new user (replace `username` and `password`):
```sql
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```
3. Grant the new user all privileges:
```sql
GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```







