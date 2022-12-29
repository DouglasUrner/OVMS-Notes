# Hosting an OVMS Server V3 on a free Oracle Cloud instance.

## Instance Configuration

### Basic 

Ubuntu

sudo apt update
sudo apt upgrade
reboot if necessary

sudo apt install build-essential

### Firewall

Open Ports for:
* Nginx (used to prove to Let's Encrypt (via Dehydrated) that we are who we say we are): 80
* OVMS V2:
  * OVMS APP: 6867
  * REST API: 6869
  * OVMS MP: 6870
* OVMS V3:
  * 8883 (TLS)

### Configure to use SSL

Using a Let's Encrypt certificate. To validate the certificate you'll need a webserver (hence Nginx) and Dehydrated to handle renewal of the certificate.

#### Nginx

#### Dehydrated

Install Dehydrated: sudo apt install dehydrated

Then, in `/etc/dehydrated/config`, set `WELLKNOWN="/var/www/html/.well-known/acme-challenge"`

Create `/etc/dehydrated/domains.txt` with the contents: "the FQDN of your instance".
 
sudo mkdir -p /var/www/html/.well-known/acme-challenge
 
`sudo dehydrated -c`

'sudo /usr/bin/dehydrated --register --accept-terms`

#### Merge the certificate

Let's Encrypt delivers the certificate as two files, the OVMS server expects the certificate to be in a single file, so after renewal, you'll need to cat them together. Set up a chron entry to do this for you.

## Installing OVMS Server

git clone

### Database

1. Install MariaDB: 'sudo apt install mariadb-server'
2. Update / install most of the Perl libraries using `apt`:
3. Install Crypt::RC4::XS from CPAN: `sudo cpan Crypt::RC4::XS`

