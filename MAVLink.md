Notes for MAVLink:

  * The MAVLink protocol works for both ArduCopter2 users and ArduPilot Mega users
  * PID tuning through the setup menu is only for ArduCopter2, as I am not yet familiar with the needs for ArduPilot users.
  * Any system can use the parameter activity to edit any exposed parameter.

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/params.png' width='240' height='400' />

The MAVLink library I created used JNI to use the native MAVLink library and exposes it to Java.
As long as you are able to use JNI in your code, feel free to download the jMAVLink library through  http://copter-gcs.googlecode.com/files/jMAVLink.zip.