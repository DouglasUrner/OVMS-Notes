# Hosting an OVMS Server V3 on a free Oracle Cloud instance.

## Instance Configuration

### Basic 

Ubuntu

### Firewall

Open Ports for:
* Nginx (used to prove to Let's Encrypt that we are who we say we are): 80
* OVMS:
  * OVMS APP 6867
  * REST API: 6869
  * OVMS MP: 6870

### Configure to use SSL

Nginx
Dehydrate

## Installing OVMS Server

sudo apt update
sudo apt upgrade
reboot if necessary

sudo apt install build-essential

### Database

1. Install MariaDB: 'sudo apt install mariadb-server'
2. Update / install most of the Perl libraries using `apt`:
3. Install Crypt::RC4::XS from CPAN: `sudo cpan Crypt::RC4::XS`

