# Instrument Structure
*found under `/MIDIAnimator/src/instrument.py`*

```{eval-rst}
.. py:class:: Instrument

    .. py:method:: __init__(self, midiTrack: MIDITrack, collection: bpy.types.Collection, override=False)
        
        Takes a :class:`MIDITrack` and a :class:`bpy.types.Collection` and creates a new instrument 
        (that gets added to the :class:`BlenderAnimation` internal list of instrumnets)
        
        If override is ``True``, the animate method will be overwritten.
        
        :param midiTrack: The MIDI track to create the instrument from.
        :type collection: :class:`bpy.types.Collection`
        
        :param collection: The collection (:class:`bpy.types.Collection`) of Blender objects.
        :type midiTrack: :class:`MIDITrack`
        
        :param override: If true, the animate method will be overwritten.
        :type override: bool

    .. py:method:: __post_init__(self)
        
        This method only gets called if ``override`` is False.
        
        :return: None

    .. py:method:: _makeObjToFCurveDict(self)
        
        Internal method to create a dictionary of Blender objects to FCurves.
        
        Pulls Blender objects from :class:`bpy.types.Collection`.

        :return: A dictionary of Blender objects to FCurves.
        :rtype: dict

    .. py:method:: createNoteToNoteAnimatorTable(self, fCurveDict: dict)
            
        Maps a :class:`MIDINote` note number to a list of :class:`NoteAnimator` objects.
        
        :param fCurveDict: A dictionary of Blender objects to FCurves.
        :type fCurveDict: dict

        :return: None

    .. py:method:: preAnimate(self)
            
        This method gets called before the animation is started.
        
        For instance, if you wanted to remove all of the keyframes on the objects, this would be the place to do it.
        
        :return: None

    .. py:method:: preFrameLoop(self)
            
        This method calls the ``createFrameRanges()`` method, and then calls the ``preAniamte()`` method.
        
        For instance, if you wanted to remove all of the keyframes on the objects, this would be the place to do it.
        
        :return: None
    
    .. py:method:: postFrameLoop(self)

        This method clears all of the instance variables.
       
        :return: None

    .. py:method:: animateFrames(self, offset: int)
        
        This method creates keyframes for the animation. Calls the ``animate()`` method for each frame.

        :param: offset: Amount to add to the frame number for each keyframe (in case we have negative keyframes).
        :type offset: int
        
        :return: None

    .. py:method:: updateActiveObjectList(self, frame: int, offset: int)
        
        This method updates the list of active objects for a given frame.
        
        :param frame: The frame number.
        :type frame: int
        
        :param offset: Amount to add to the frame number for each keyframe (in case we have negative keyframes).
        :type offset: int

        :return: None
    
    .. py:method:: createFrameRanges(self) -> list
        
        This method creates a list of frame ranges for each note in the animation.
        
        :return: list of :class:`FrameRange` objects.
        :rtype: list

    .. py:method:: animate(self, frame: int, offset: int)
        
        This method gets called for each frame.
        Alternatively, this method can be overwritten by the user with a custom method.
        
        :param frame: The current frame number.
        :type frame: int

        :param offset: Amount to add to the frame number for each keyframe (in case we have negative keyframes).
        :type offset: int
        
        :return: None

```
