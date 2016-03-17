# Main Screen Connection #
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/notConnected.png' width='240' height='400' />
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/connect.png' width='240' height='400' />
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/main_context.png' width='240' height='400' />

Note: Any activity can be started first (if you write your own launcher).
As such, any activity will automatically start the connect prompt if not connected.

This first time you start the app, it will ask you to select the bluetooth modem.
It will remember this selection, and attempt to auto-connect from this point forward.
You can "forget" this modem by using the settings menu and selecting "Forget Modem".
In the same menu you can also force a connection attempt.

Similarly, on first connect, if will ask you to specify the protocol to expect: MAVLink or AC1.
Again, this can be changed later using the context menu.

# Status #

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/status.png' width='240' height='400' />
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/gpsModeStatus.png' width='240' height='400' />
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/statusMAVLink.png' width='240' height='400' />


This shows the current status of the copter, eliminating the guess work about which mode it is in.
No GPS lock when I did this. Press and hold any line of text to refresh the information.
The right most screen shows the new MAVLink status page.

# Graphing of outputs #
(Looks better when live, the frame capture causes some gaps):

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/readouts.png' width='400' height='240' />

Note: Pinch (two finger) or stretch the screen to zoom in/out.
Drag the slider to increase/decrease the scroll rate (stretches/squashes to fill the screen)

# Setup #

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/PIDS.png' width='240' height='400' />
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/hardware_setup.png' width='240' height='400' />
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/transmitter.png' width='240' height='400' />

This section lets you:

**PIDS**

Adjust PID settings for each of the modes. Very useful in the field for tuning.
Some work remains for easily selecting values. I've tested Stable mode extensively, the others should work properly as well, but take it slowly.
For MAVLink, this page is auto-generated based on the received parameters. This makes it compatible with both planes and quads.

**Hardware**

As expected, these let you setup each of the hardware options. Once satisfied, simply hit save. A confirmation message will be shown once all entries saved.

**Transmitter**

For MAVLink, when you open the activity, the currently calibrated values are shown for min/max.

This section performs the standard calibration:
1. Select "Start Calibration"
This removes the current calibration
2. Move each of the controls to their extremes.
As you move them, each Min/Max will turn green to indicate you adjusted them. This is important, only green entries will be saved!
When satisfied, select "Save Calibration".
For MAVLink, a notification will be shown indicating successull calibration.

For AC1
When your transmitter is in the "Neutral" position, that is no pitch or yaw, it won't always actually be 1500.
I've added a few lines of code to the GCS.pde file, which allows you to set the neutrals for pitch, roll and yaw.
For arducopter users (not MAVLink), add the following to your GCS.pde file, in the readSerialCommand() function:
```C

//--------------------------
// Enable midpoint selection
case '6':
roll_mid = ch_roll;
pitch_mid = ch_pitch;
yaw_mid = ch_yaw;
//--------------------------
```


For MAVLink and AC1
Select "Save Midpoints" to set the neutral positions of the transmitter.

**Offsets (AC1 Only)**

This lets you either manually set the offsets (upper section, like the standard calibration), or using the "Counter Drift" section.
In "Counter Drift", line up the phone to match the APM, and observe which way the quad tends to drift.
Then simply offset in the opposite direction. That is, if it drift right, press the left button a few times.
Each time, save the offsets and observe the changes.
This feature is here mostly because when im outside I had a hard time remembering which offset/direction would correct the observed drift.




# GPS #
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/GPSSample.png' width='400' height='240' />

The GPS mode shows the current phone location (Blue dot, with a "certainty" bubble).
Android will use a phone tower, WIFI or GPS, depending on which is available, and has best accuracy.

The Quad GPS is mapped with the red pin, and shows the past 100 location fixes as a trail.
The pin is updated each time GPS data is received.

A point is added to the trail when the quad has moved at least 3m, in order to reduce the number of data points.
When a point is added to the trail, it is also saved to the SD card in the folder "QuadCopter"
Note that the GPS view has to be active for this log to be kept!
Longitude, Latitude and Altitude are saved, for now just in simple text format, eventually I wil likely pick some standard format.

# Parameters #
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/params.png' width='240' height='400' />

For MAVLink only. Lets you change any parameter for the quad.

# HUD #
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/hud.png' width='400' height='240' />

As you would expect, this activity shows you the orientation and useful info in one display.
Note: Due to limitations with streaming data using AC1, when connected with AC1 you only get the orientation (pitch/yaw) updates.
All the other bits are disabled, as I can't get AC1 to stream them all at the same time.

# Mode Selection #

MAVLink only
This mode shows the current switch position in yellow, as well as the mode selection for each switch position.

<img src='http://copter-gcs.googlecode.com/svn/wiki/img/mode_selection_a.png' width='240' height='400' />
<img src='http://copter-gcs.googlecode.com/svn/wiki/img/mode_selection_2.png' width='240' height='400' />

Selecting a switch entry shows the various options.
This allows you to set the mode for that position. As soon as selected, it will be saved to the quad.

