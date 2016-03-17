NEWS


---

February 10, 2012

New note for arduPlane users:

A question came up about using copter-gcs with planes.
Short answer: It will work partially for certain, but verify with mission planner the first time you change settings.

The following are some more detailed notes:
  * Transmitter calibration should work fine, as is should be the same.
  * PID tuning is auto-generated from MAVLink messages. If arduplane follows the same message naming convention, it will work fine.
  * MAVLink Params will certainly work without issue. Keep in mind that parameters as shown on the mission planner may be scaled or altered before being sent out over MAVLink (I.e., the declination is stored in radians, but shown in degrees). Copter-GCS simply shows the raw data.
  * The HUD and GPS/mission readouts should work fine

Best thing to do the first time is to set parameters using copter-gcs, and then verify in mission planner (or the other way around)

As always, this is all "use at own risk".

Happy flying


---

November 15, 2011

Released Version 7:

Changes:
  * The mode selections are corrected
  * MAVLink updated to the latest version.

For those interested (as before), although copter-gcs is aimed at copters, many portions of it are certainly compatible with fixed wings as well.


---

October 26, 2011
Just reached 200 downloads on version 6, thought I'd highlight the milestone :)


---

August 7, 2011

Big new release (5), some bug fixes and lots of new features.

  * The transmitter bug is taken care of.
  * Force orientation (Portrait or Landscape) for tablet users.
  * Transmitter Mode setup is available now. It also shows what the switch is currently set to.
  * Mission display and editing capabilities.

There is also a google group (http://groups.google.com/group/copter-gcs). If you subscribe, I can send out bug info and notify you of new releases.

As always, use at your own risk.
I try to keep bugs out, but when trying something new, doing so without props the first time is a good idea.
The AC2 code is still changing, so some features may stop working (as was the case for PID tuning for a bit) but will be fixed in the next release.


---

August 5, 2011

A bug with the transmitter calibration (in version 4, mavlink) has come up. Please don't use it until the next release!
Sorry for the inconvenience.


---

July 20, 2011

There is an experimental copy of the code in SVN which attempts to access an XBee module attached through USB host mode on Android 3.0+ tablets.
It allows selection of the USB device, opens it, and is tied in to send/receive data just like a bluetooth connection. However, it doesn't actually work...

It appears USB host mode does not currently support USB->Serial converters, as the kernel module for it is not loaded.
Once a kernel module is made available (by default, and not through hacks) which supports FTDI chips, I will revisit this code and bring it into the main branch.

A big thanks goes to Jeff E (on the DIYDrones site) for repeatedly running the code for me on his tablet.
With the logs he collected I was able to write enough code such that when USB->Serial is supported by the Android OS, the app will quickly be able to support it also.
The posted code wouldn't have gotten there without his help.

If anyone has leads on how to make android / USB Serial work, please let me know!


---



&lt;FIXED&gt;

 I just found a bug with the latest release where MAVLink PIDs don't save when using the PID activity.
I'm fixing it, but in the mean time the Parameter mode lets you access them as well, and it works fine.


---

July, 2011

Bug Fixes:

  * PID tuning saves properly for MAVLink.
  * HUD roll reversed.


---

July 9, 2011

Version 0.91 finally released!
New features:

  * MAVLink support for both ArduCopter 2 and Ardu Pilot Mega (Fixed wing)
  * HUD display
  * Parameter editing (MAVLink)

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/hud.png' width='400' height='240' />

There will be some changes coming to the PID section, as IMAX is not exposed for any of the PIDs.
I also want to make some useability changes to the PID section. This release will get people started though.

Things I'm thinking about:
  * I want to start work on Mission Planning soon, so keep an eye out.
  * Host mode for tablets has been mentioned as a desired feature. No promises right now, but it is a thought.
  * Wifi access using a Wifi->serial module. Not on the todo list at the moment, but it is a thought.


---

June 9, 2011

Version 0.9 is now available through both the [Android Market](https://market.android.com/details?id=com.bvcode.ncopter), and the download page.
The Android Market version costs $5, mostly to offset the cost of making it available on the market in the first place.
It is identical to the code / download version, but will get you automatic updates, and a very simple install processs.
Please let me know if you have any issues, but i've had great success on my phone (Nexus S).

Note that GPS, Internet access (for the maps), and Bluetooth are required for use.
Enjoy


---

Available install routes:

  * Install from Android Market ($5) [Copter-GCS](https://market.android.com/details?id=com.bvcode.ncopter)
  * Install the APK from the download section
  * Build from source, following roughly the following steps:

  1. Install the environment:
> > http://developer.android.com/sdk/installing.html

  1. Setup google maps (this also details the api-key stuff):
> > http://code.google.com/android/add-ons/google-apis/maps-overview.html

  1. Once these are done, using svn in eclipse, download the code from
> > http://code.google.com/p/copter-gcs/source/browse/droid-gcs

  1. Build and install, and it should work. Note that this path is for developers interested in the code.

---


Note that to use the source version that you will need to replace the GoogleMaps "android:apiKey" with your own in the file "res/layout/gps\_view.xml".
Look here for how to get it: http://code.google.com/android/add-ons/google-apis/mapkey.html.

I found using a laptop in the field awkward (as mine is dying).
My phone has plenty of power to handle the copter interface.

Xbee's (900mhz in my case) are commonly used for telemetry, but they don't provide a convenient interface to a phone. Even if a cable existed, that would be annoying.

Instead, I built a little XBee to Bluetooth bridge, powered off an old transmitter battery.

Based on power consumption of the modules, I expect around 15+ hours of life, so clearly enough for a day of fun.

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/GPSToCome.png' width='180' height='300' />
<img src='http://img26.imageshack.us/img26/4071/img20110426235731.jpg' width='400' height='300' />
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/PIDS.png' width='180' height='300' />