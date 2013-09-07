PiBot
===

## Early ages control
### Cards
#### Optical Tracking (Above)
- Augmented Reality.
- Tripod raising camera up to look down on a desk.
- Fold away mat with a grid?
- Can be easily projected on a board.

#### Optical Tracking (Below)
- [Microsoft Pixelsense](http://www.microsoft.com/en-us/pixelsense/default.aspx)

- Physical pices of transparent glass or plastic that can be projeted on but still have a tag the under-camera can read.
- Can print information on the card such as Forward, Right Turn, etc.
- Variables such as number of steps to take forward can be projected on to the physical object.

- SMART Table doesn't seem to support this kind of tracking.
- Samsung SUR40 costs about £8,000.

All in all probably one of the better methods but it's so expensive to do.

#### RFID/NFC
- Needs lots of readers. (Expensive!)
	- Costs can be brought down by some [clever multiplexing](http://www.thebox.myzen.co.uk/Hardware/RFID_Sequencer.html).
- Fixed size.
- Requires large, single purpose board to place cards on.
- Requires specially made cards.
	- Not too hard to get done in bulk.

#### Physical connection blocks
- Expensive per module.
- Large and bulky.
- Will require some kind of host device.

## SMS control
Random little hack that allows students to text small logo-style programs to the PiBot using [Twilio](https://www.twilio.com), doesn't quite work but it's mostly there.

## Web Interface

### Remote driving
- WebRTC, WebSockets or something like that for live control.
- WebRTC can do video, see if it's possible to throw the Pi camera video back.
- Google Chrome and Firefox have a [gamepad API](http://www.html5rocks.com/en/tutorials/doodles/gamepad/), appears to work on Chromebooks with the Xbox 360 wired and wireless controller.

### Remote programming
- Local interface with drag and drop.
- Local interface with HTML5 text editor that a Pi-side interpreter (Python, Node, etc) runs.
- Cloud based IDE (Cloud9?) that deploys to the Pi.
- git, SVN or other code mangment that students push to then the Pi pulls from.
- Write a file and upload it.

## Loading programs without network connectivity
- USB Autorun
	- BAD IDEA
- NFC
	- NFC card programmed with short programs.
	- NFC cards loaded direct from an NFC capable device.
	- Security mostly in the rage (2-3cm).
- Bluetooth
	- Good for current iOS devices.
- SD card
	- Requires turning off and on every time.
- IR
	- REALLY slow.
	- Requires transmitter that isn't on many devices anymore.
	- Remote programming would be really clunky.
	- Prone to interference.
- Sound
	- Not in a noisy classroom.
- Visual markers
	- Hold something like a QR code containing program in front of PiBot.
	- Something like how Aibo's visual cards worked?
- Buttons/keypad

## Hardware changes
- Motor wires thinner or terminal blocks larger.
- Battery solder pads larger.

## Networking

### WiFi APs
TP-Link TL-WR702N (Tiny, blue, no USB)  
TP-Link TL-WR703N (Tiny, blue, USB) - For the chinese market, doesn't seem to be legal to sell in US/UK.  
TP-Link TL-WR710N (Plug sized, USB)  
TP-Link TL-MR3020 (Small, grey, USB)  

### Connecting to a network
- Manually with a TV, keyboard and mouse.
	- Little bit of a problem for the out of the box experience.
- WPS
	- Really don't want to do this, also insecure.
(See loading programs for more ideas on this)

### Zeroconf/Bonjour mDNS
Used to create a fixed name that the PiBot can be accessed from internally.  
Something like **pi@PiBot-[serial].local** that is consistent across networks.  
Pull the serial number from the Pi's SoC.  
Works on OS X and iOS, need to test ChromeOS again, Windows doesn't seem to like it so much but working on that.  

#### Install
	sudo apt-get install avahi-daemon

Also work out how to set the hostname to the SoC serial in a predictible and repeatable way.