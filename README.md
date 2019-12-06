# [Traccar](https://www.traccar.org)

## Overview

Traccar is an open source GPS tracking system. This repository contains Java-based back-end service. It supports more than 170 GPS protocols and more than 1500 models of GPS tracking devices. Traccar can be used with any major SQL database system. It also provides easy to use [REST API](https://www.traccar.org/traccar-api/).

Other parts of Traccar solution include:

- [Traccar web app](https://github.com/traccar/traccar-web)
- [Traccar Manager Android app](https://github.com/traccar/traccar-manager-android)
- [Traccar Manager iOS app](https://github.com/traccar/traccar-manager-ios)

There is also a set of mobile apps that you can use for tracking mobile devices:

- [Traccar Client Android app](https://github.com/traccar/traccar-client-android)
- [Traccar Client iOS app](https://github.com/traccar/traccar-client-ios)

## Features

Some of the available features include:

- Real-time GPS tracking
- Driver behaviour monitoring
- Detailed and summary reports
- Geofencing functionality
- Alarms and notifications
- Account and device management
- Email and SMS support

## Installation Guide
Before starting the installation make sure that you have a cloud server running Ubuntu, or any Linux Distribution.

### Installing default build
Follow the instructions on this [link](https://www.traccar.org/install-digitalocean/) to install the default build on any Linux cloud server.

#### Downloading Traccar package for Linux
Check that you're downloading the latest Linux version everytime. 
```
Correct as at: 5/12/2019
https://github.com/traccar/traccar/releases/download/v4.6/traccar-linux-64-4.6.zip
```
#### Replace default config file
Replace the default config file with the one found in this repository, using the same instructions as stated in the link.

#### Starting the service and check status
```
sudo systemctl start traccar.service
sudo systemctl status traccar.service
```

### Installing dependencies
1) installing Java and Maven:
```
$ sudo apt install default-jdk
$ sudo apt install maven
```
2) Go to root directory ` cd ~`. Installing Sencha
```
$ wget http://cdn.sencha.com/ext/gpl/ext-6.2.0-gpl.zip
$ unzip ext-6.2.0-gpl.zip
$ wget http://cdn.sencha.com/cmd/6.2.1/no-jre/SenchaCmd-6.2.1-linux-amd64.sh.zip
$ unzip SenchaCmd-6.2.1-linux-amd64.sh.zip
$ sudo ./SenchaCmd-6.2.1.29-linux-amd64.sh -q -dir /bin
```

### Installing Custom Traccar Build
1) Go to root directory `cd ~`. Clone this repository via the following command.
```
git clone --recursive https://github.com/chweeee/traccar
```
#### Replacing default back-end with custom build
1) Change into the `traccar` directory and build from source code.
```
cd traccar
mvn package
```
2) You will see a file ending with `.jar` in `traccar/target`. Replace `.jar` file in `/opt/traccar` with this file.

3) repeat step 1 to 2 whenever changes are made to the back-end source code.

#### Replacing default front-end with custom build
1) Change into the the traccar-web repository.
```
cd /home/ubuntu/traccar/traccar-web/tools 
```
2) Build from source.
```
./minify.sh
```
3) Copy the entire `web` folder over to `/opt/traccar`.
```
sudo cp -r /home/ubuntu/traccar/traccar-web/web /opt/traccar
```
4) repeat step 1 to 3 whenever changes are made to the front-end source code.

