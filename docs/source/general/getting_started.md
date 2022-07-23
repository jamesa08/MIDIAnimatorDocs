(getting_started)=

# Getting Started

To start writing your own MIDI Animation programs, first, open a Text Editior window.

```python
import bpy
from MIDIAnimator.src.animation import BlenderAnimation
from MIDIAnimator.data_structures.midi import MIDIFile

file = MIDIFile("/path/to/midi/file.mid")
pianoTrack = file.findTrack("Steinway Grand Piano")

animator = BlenderAnimation()
animator.addInstrument(midiTrack=pianoTrack, objectCollection=bpy.data.collections['Cubes'], custom=CustomInstrument)

# Animate the MIDI file
animator.animate()
```

<br>

Next, run the program. You then should see animation data for the objects that you specified in the script.

Any objects that previously have animation data will be overwritten.



## Writing Custom Animation Functions

```python
import bpy
from MIDIAnimator.src.animation import BlenderAnimation
from MIDIAnimator.src.instruments import Instrument
from MIDIAnimator.data_structures.midi import MIDIFile

class CustomInstrument(Instrument):
    def __init__(self, midiTrack: MIDITrack, collection: bpy.types.Collection, **kwargs):
        super().__init__(midiTrack, collection, override=True)
    
    def animate(self):
        # Write your custom animation here...
        pass

file = MIDIFile("/path/to/midi/file.mid")
pianoTrack = file.findTrack("Steinway Grand Piano")

animator = BlenderAnimation()
animator.addInstrument(midiTrack=pianoTrack, objectCollection=bpy.data.collections['Cubes'], custom=CustomInstrument)

# Animate the MIDI file
animator.animate()
```
