
  This driver also works with my Epever Triron 4210n.
  
  The new Rasperry Pi operating system, Bookworm 12, has a driver designated 'ttyUSB0.'
  Historically, getting a driver for the Epever charge controllers' Exar chip to run has been 
  difficult, at best.
  First, there was kasbert's driver source code. Then Maxlinear bought out Wxar and developed two 
  new drivers, on for older linux kernels and on for newer kernels.
  After I installed Bookworm lite on my Rasperry Pi 4b-2Gb, I tried kasbert's code but could not 
  get an easy compile. Then I tried the Maxlinear code for newer linux kernels. That code compiled 
  but would not insert using 'insmod.'
  After a discussion kasbert, developed new code which compiles easily and works with a caveat. 
  The code is written to allow the user to send and receive data frim the command line.
  The problem, for me was getting the code to run during boot without user interaction. I could 
  get the code to run but the first two accesses would fail but work correctly thereafter.
  I tracked down some code embedded in an article on rs-485 communications on the linux docs site. 
  I extracted the code, made minor modifications and compiled the code which ran readily and 
  without error or intervention.
  My use involves calling the code from a php script. The executable path was made part of the 
  system PATH beforehand. All scripts of all languages can access the driver once the first call 
  has been made, hence the need for an initial call during boot.

  Add a call to a script or systemd service.
  Make a folder to hold the code and compile.
  Add the path to system PATH. I keep all my scripts and code in '/var/www/html/', created by the 
  Apache server since much of my work is web related.
  Reboot.
  Call the exec from within a script or systemd service.
