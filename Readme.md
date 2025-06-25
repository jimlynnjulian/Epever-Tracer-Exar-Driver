
  This driver also works with my Epever Triron 4210n.
  
  The new Rasperry Pi operating system, Bookworm 12, has a driver designated 'ttyUSB0.'
  Historically, getting a driver for the Epever charge controllers' Exar chip to run has been 
  difficult, at best.
  First, there was kasbert's driver source code. Then Maxlinear bought out Exar and developed two 
  new drivers, on for older linux kernels and on for newer kernels.
  After I installed Bookworm lite on my Rasperry Pi 4b-2Gb, I tried kasbert's code but could not 
  get an easy compile. Then I tried the Maxlinear code for newer linux kernels. That code compiled 
  but would not insert using 'insmod.'
  After a discussion kasbert, developed new code which compiles easily and works with a caveat. 
  The code is written to allow the user to send and receive data from the command line.
  The problem, for me was getting the code to run during boot without user interaction. I could 
  get the code to run but the first two accesses would fail but work correctly thereafter.
  I tracked down some code embedded in an article on rs-485 communications on the linux docs site. 
  I extracted the code, made minor modifications and compiled the code which ran readily and 
  without error or intervention.
  My use involves calling the code from a php script. The executable path was made part of the 
  system PATH beforehand. All scripts of all languages can access the driver once the first call 
  has been made, hence the need for an initial call during boot.

  Add a call to an initialization script or systemd service.
  Make a folder to hold the rs485b code, and compile.
  Add the path to system PATH. 
  Reboot.
  Call the exec from within scripts or systemd services.


  pi@raspberrypi-ssd:~ $ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13fd:0840 Initio Corporation INIC-1618L SATA <--- enclosure for USB SSD
Bus 001 Device 003: ID 04e2:1411 Exar Corp. XR21B1411 UART  <--- Exar driver pre-installed by opsys Bookworm May-13-2025 release.
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


