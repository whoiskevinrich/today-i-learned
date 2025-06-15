# Uncomplicated Firewall (UFW)

Uncomplicated Firewall (UFW) is a user-friendly interface for managing firewall rules in Linux. It is designed to make managing a netfilter firewall easier, providing a command-line interface for configuring the firewall.

## Installation
UFW is typically pre-installed on Ubuntu systems. If it is not installed, you can install it using the following command:

```bash
sudo apt install ufw
```

## Basic Configuration

### Enabling UFW
To enable UFW, use the following command:

```bash
sudo ufw enable
```

### Enabling SSH from home network
To allow SSH connections from your home network, you can specify the IP address or subnet.

```bash
sudo ufw allow ssh
sudo ufw allow from 192.168.1.0/24
```

### Allowing Specific Ports
To allow specific ports, you can use the following command:

```bash
sudo ufw allow from 192.168.1.0/24 to any port 8080
```