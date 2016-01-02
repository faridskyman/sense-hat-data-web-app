# Sense HAT Data Web App

Log Sense HAT sensor data and show it in a web app

## Requirements

### Hardware

- Raspberry Pi
- Sense HAT

### Software

- Flask
- Sense HAT Python library

Advanced version:

- Apache
- Apache mod WSGI
- Weaved

```bash
sudo apt-get install sense-hat python-pip apache2 libapache2-mod-wsgi weavedconnectd
sudo pip install flask
```

## Usage

### Simple: LAN

The simple version can be run on a LAN, so you can view the Flask web app on any device on your local network.

Clone this repo and run `db.py` in cron to store data, then run `app.py` and run the web app:

```bash
git clone https://github.com/bennuttall/sense-hat-data-web-app
cd sense-hat-data-web-app/www
python db.py # use cron to run this regularly
hostname -I # keep note of this IP address
python app.py # now navigate to the IP address in a web browser on any device on your network (e.g. `http://192.168.1.3`)
```

### Advanced: Internet

Using Apache and mod WSGI to serve the Flask web app, you can connect to Weaved to open your Pi to the web.

- See [Weaved documentation](https://www.raspberrypi.org/documentation/remote-access/access-over-Internet/internetaccess.md), [sign up](http://www.weaved.com/), install on your Pi and configure web service
- Install Apache and mod WSGI as above
- Configure `/etc/apache2/sites-available/000-default.conf` as per [apache/000-default.conf](apache/000-default.conf)
- Get your Pi's web address from Weaved (e.g. `https://abcdefgh.p19.weaved.com/`)
- Navigate to it in a web browser
