This project aims to provide a GCS for the arduCopter and arduPirate copters, using an android smart phone.
Since phones generally come with Bluetooth connectivity, it makes sense to use that for communication. Obviously the typical range for Bluetooth is poor, so the standard XBee modules make more sense for the long haul connection. Combining them then, is needed for a convenient phone based GCS.

<img src='http://img26.imageshack.us/img26/4071/img20110426235731.jpg' align='center' width='400' height='300' />

A Bluetooth to XBee bridge

Current features include:
  * PID configuration
  * Transmitter calibration
  * Accelerometer offset calibration
  * Sensor readouts
  * Live copter status, with flight mode.
  * GPS mapping

Planned/Thinking about:
  * GPS following
  * GPS Waypoint entry
  * GPS Logging
  * Constant GPS offset from operator (phone with GPS)
  * Sonar/Barometer altitude settings