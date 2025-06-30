  

This driver is derived from code found online in a linux source archive.
The driver works with Epever Triron 4210n. The Tracer series may also work.

Make a folder, insert the code, and compile. No downloads or installations shoiuld be needed.
Make a systemd service to run the driver during the boot process.
Make the service a one-shot.
From then on, the driiver should work without intervention.
I use the driver with PHP & python scripts.
Note, you may have to make an adjustment if you need to work in a virtual python environment.
Since no libraries are used, no virtuall environment should be needed.


The Exar listing below occurs because the Epever charge controller is plugged into  USB port.

1. pi@raspberrypi-ssd:~ $ lsusb
2. Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
3. Bus 001 Device 004: ID 13fd:0840 Initio Corporation INIC-1618L SATA <--- enclosure for USB SSD
4. Bus 001 Device 003: ID 04e2:1411 Exar Corp. XR21B1411 UART  <--- Exar driver pre-installed by opsys Bookworm May-13-2025 release.
5. Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
6. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


