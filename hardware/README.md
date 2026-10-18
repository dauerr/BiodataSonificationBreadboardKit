# Biodata MIDI board definitions

The Arduino Uno has no native USB (its USB port is a serial converter), so it cannot show up as a
USB MIDI device. Boards with an ATmega32U4 (Arduino Leonardo, Arduino Micro) can: when the sketch is
compiled for one of them, every MIDI message sent to the MIDI out jack is also sent over USB MIDI.

The USB device name comes from the board definition, not from the sketch. These boards are the
stock Leonardo / Micro with the USB product name set to **Biodata MIDI**.

## Install

1. Install "Arduino AVR Boards" in the Boards Manager, and the libraries EEPROMex, Bounce2,
   LEDFader and **MIDIUSB** in the Library Manager.
2. Copy the `biodata` folder into the `hardware` folder of your sketchbook
   (create it if needed), e.g. `~/Documents/Arduino/hardware/biodata/avr/boards.txt`.
3. Restart the Arduino IDE and select **Tools > Board > Biodata MIDI (Arduino Leonardo)**
   (or Micro), then upload.

With arduino-cli: `--fqbn biodata:avr:biodata_leonardo`.

## Wiring differences from the Uno

- MIDI out jack: TX pin 1 (`Serial1`), same pin as on the Uno.
- Galvanometer (555) input: pin 2, same as on the Uno.
- LEDs on pins 3, 5, 6, 9, 10, 11 and the knob/button on A0/A1 are unchanged.

Windows caches device names per USB VID/PID; if it still shows "Arduino Leonardo", remove the
device in Device Manager and plug it in again.
