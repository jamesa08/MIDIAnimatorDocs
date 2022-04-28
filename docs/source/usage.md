# Usage

(installation)=

## Installation

You will need to install Blender (version 2.91 or better) to use MIDI Animator.

1. Download the `.zip` file in the Releases pane, or click [here.](https://github.com/imacj/MIDIAnimator/releases)
2. In Blender, go to Edit -> Preferences
3. Next, go to Add-ons -> Install...
4. Locate the `.zip` file
5. Close the preferences pane.
6. Volia! You have now successfully installed MIDI Animator.

(getting_started)=

## Getting Started

To start writing your own MIDI Animation programs, first, open a Text Editior window.

```py
# Unfinished. Subject to change.
from MIDIAnimator import MIDINode

midiFile = "/Users/james/Desktop/twinkle.mid"

node = MIDINode(midiFile)
node.addInstrument("bounce", "PianoTrack" "piano_keys")

# Animate the MIDI file
node.animate()
```

<br>

Next, run the program. You then should see animation data for the objects that you specified in the script.<br>
Any objects that previously have animation data will be overwritten. This can be disabled by enabling the flag `noOverwrite` on the `MIDINode.animate()` function to `True` (e.g., `MIDINode.animate(noOverwrite=True)`).

## Writing Custom Animation Functions

Unfinished.

```py
# Unfinished. Subject to change.
from MIDIAnimator import MIDINode

midiFile = "/Users/james/Desktop/drums.mid"

node = MIDINode(midiFile)
node.addInstrument("custom", "DrumTrack", "Drums_animate")

data = node.getMIDIData()
timesOn = []
timesOff = []

for instrument in data:
    for track in instrument:
        # do something

# TODO: somehow pass the "animated" data into the MIDINode?
# how should the animated data be represented?

note.animate()
```

## Animation Types (subject to change)

<br>
Bounce animation. Pre-defined animation code that animates a "bounce". Parameters: Pass in a FCurve data object.<br>
Hi-Hat animation. Pre-defined animation code that animates how a hi-hat moves.<br>
Drumstick animation. Pre-defined animation code that animates how drumsticks move and feel. More complex<br>
Custom animation. <br>
<br>
