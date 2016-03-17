<img src='http://img26.imageshack.us/img26/4071/img20110426235731.jpg' width='750' height='562' />

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/JeffE.JPG' width='750' height='500' />

The first shot is Bart's copter-link, the second one is a nice compact version by Jeff E.
This provides the link between phone and copter, merging the advantage of the long range of the XBees and the phone compatibility of Bluetooth.

The wiring is easy enough, power into the regulator, 3.3v out. Cross the Tx/Rx lines on the two modules and all good.

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/wiring.png' width='800' height='370' />

Parts List:
http://www.robotshop.com/ca/spark-fun-bluesmirf-3.html

http://www.robotshop.com/ca/sfe-xbee-explorer-regulated-3.html
Note: If using 900mhz modules, remove/short the diode on the Din line. It causes garbled data from the quad. Removing it works great.

http://www.robotshop.com/ca/dimension-engineering-de-swadj.html
Note: I ended up using ~3.3v as that made the XBee and Bluetooth run at the same voltage (the explorer only level shifts on the way in, if I recall right).


# Notes #

Some people have had trouble setting up the link. A few lessons learned:

  * Make sure your baud rate it set to 56K in the bluetooth module
  * If you get a heartbeat, but nothing else works, then you are only receiving data. The send portion of your link (to the quad) is not working. Generally this has been the "diode on the Din line" problem with the XBee explorer.
  * Make sure the bluetooth module is set to 56k; it may not ship at the correct baud rate.