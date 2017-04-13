unifi-freenas
=============

This is a fork of the fantastic script from here
https://github.com/gozoinks/unifi-pfsense

The underlying script is the same as the pfSense package, with the extra step of installing snappy-java and overwritting the shipped version.

To install the controller software and the rc script:

1. Log in to the FreeNas jail command line shell as root.
2. Run this one-line command, which downloads the install script from Github and executes it with sh (points to current 4.6.6 branch):

  ```
    fetch -o - https://raw.githubusercontent.com/TribuneX/unifi-freenas/master/install-unifi/install-unifi.sh | sh -s
  ```

The install script will install dependencies, download the UniFi controller software, make some adjustments, and start the UniFi controller.

Starting and Stopping
---------------------

To start and stop the controller, use the `service` command from the command line.

- To start the controller:

  ```
    service unifi.sh start
  ```
  The UniFi controller takes a few minutes to start. The 'start' command exits immediately while the startup continues in the background.

- To stop the controller:

  ```
    service unifi.sh stop
  ```
  The the stop command takes a while to execute, and then the shutdown continues for several minutes in the background. The rc script will wait until the command received and the shutdown is finished. The idea is to hold up system shutdown until the UniFi controller has a chance to exit cleanly.

