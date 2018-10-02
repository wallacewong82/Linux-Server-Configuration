# Linux Server Configuration

## Project Description

Take a baseline installation of a Linux distribution on a virtual machine and prepare it to host your web applications, to include installing updates, securing it from a number of attack vectors and installing/configuring web and database servers.

- IP address: 54.179.134.13

- Accessible SSH port: 2200

- Application URL: http://54.179.134.13.xip.io

## Walkthrough
### User Management 
1. Logging into the server: Go to a Linux terminal, and login as `grader` via the following command: `ssh -i ~/.ssh/LightsailDefaultPrivateKey.pem -p 2200 grader@54.179.134.13`
2. Logging in as `root` has been disabled.
3. Once logged in, you will then have `sudo` access.

### Security
1. Firewall settings: Key in `sudo ufw status` to see that the firewall has been set to allow only 3 ports: SSH (2200), HTTP(80), and NTP(123).
2. RSA key settings are required for login.
3. Application is up-to-date via keying in `sudo apt-get update` and `sudo apt-get upgrade`.
4. SSH is only via port 2200.

### Application Functionality
1. Visit site at [http://54.179.134.13.xip.io](http://54.179.134.13.xip.io)
2. Log in to the site using your Google ID, which takes you back to the main Catalog page.
3. Play around with the information already uploaded.
4. As a logged in user, you will be able to add, edit, and delete both subcatalog and item entries that you own only. 

### Software used or added
1. Program runs exclusively on Python3, and uses the following frameworks/tools: `apache2`, `flask`, `psycopg2`, `httplib2`, `oauth2client`, `virtualenv`, `mod-wsgi-py3`, and `sqlalchemy`.
2. Database used is SQLite3 (The PostgreSQL was not used).
3. Notable configurations made:
- Project borrows from my previous Udacity Full Stack Project: https://github.com/wallacewong82/Catalog_project
- Added `grader` account into `/etc/sudoers.d`
- For `/etc/apache2/sites-enabled/000-default.conf`, the WSGI daemon method was used. 
- The database file `catalog.db` had to have access rights changed to `chmod 777` for both the file and the `/html` folder housing it.
- For interest, the following error log was extremely useful: `/var/log/apache2/error.log`.

**Special Thanks to *[rrojoson](https://github.com/rrjoson/)* for his very helpful README!**
