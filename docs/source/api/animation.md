# Animation Structure
*found under `/MIDIAnimator/src/animation.py`*

```{eval-rst}
.. py:class:: BlenderAnimation

    .. py:method:: __init__(self)
        
        Takes a :class:`MIDITrack` and a :class:`bpy.types.Collection` and creates a new instrument 
        (that gets added to the :class:`BlenderAnimation` internal list of instrumnets)
        
        If override is ``True``, the animate method will be overwritten.
        
        :param midiTrack: The MIDI track to create the instrument from.
        :type collection: :class:`bpy.types.Collection`
        
        :param collection: The collection (:class:`bpy.types.Collection`) of Blender objects.
        :type midiTrack: :class:`MIDITrack`
        
        :param override: If true, the animate method will be overwritten.
        :type override: bool

    .. py:method:: addInstrument(self, midiTrack: MIDITrack, objectCollection: bpy.types.Collection, custom=None, customVars: Dict=None)
        
        Creates a new :class:`Instrument` and adds it to the :class:`BlenderAnimation` internal list of instrumnets        
        
        :param midiTrack: The MIDI track to create the instrument from.
        :type collection: :class:`bpy.types.Collection`
        
        :param collection: The collection (:class:`bpy.types.Collection`) of Blender objects.
        :type midiTrack: :class:`MIDITrack`
        
        :param custom: Pass in a custom instrument method here.
        :type custom: class

        :param customVars: Pass in custom instrument variables here to be passed in as keyword arguments to your class.
        :type customVars: dict

    .. py:method:: animate(self, offset: int=0) -> None
        
        Animates all of the instruments.

        :param offset: The offset to start the animation at, defaults to 0.
        :type offset: int
        
        :return: None

    

```
