# MIDI Structure
*found under `/MIDIAnimator/data_structures/midi.py`*

```{eval-rst}
.. py:class:: MIDINote
    
    Takes a ``channel``, ``noteNumber``, ``velocity``, ``timeOn`` and ``timeOff`` and creates a :class:`MIDINote` object.
    
    .. :attribute:: channel

        MIDI channel of the note, 0-15.
    
    .. attribute:: noteNumber
        
        MIDI note number of the note, 0-127.
    
    .. attribute:: velocity
        
        MIDI velocity of the note, 0-127.

    .. attribute:: timeOn
        
        Time the note was turned on, in seconds.

    .. attribute:: timeOff
        
        Time the note was turned off, in seconds.
    

.. py:class:: MIDIEvent
    
    Takes a ``channel``, ``value``, ``time`` and creates a :class:`MIDIEvent` object.
    
    .. :attribute:: channel

        MIDI channel of the note, 0-15.
    
    .. attribute:: value
        
        MIDI value of the event, 0-127.
    
    .. attribute:: time

        Time the event occurred, in seconds.

.. py:class:: MIDITrack
    
    .. py:method:: addNoteOn(self, channel: int, noteNumber: int, velocity: int, timeOn: float) -> None
        
        adds a Note On Event
        
        :param int channel: the MIDI Channel the note is on
        :param int noteNumber: the note number, range from 0-127
        :param int velocity: the note velocity, range 0-127
        :param float timeOn: the note time on, in seconds

    .. py:method:: addNoteOff(self, channel: int, noteNumber: int, velocity: int, timeOff: float) -> None
        
        adds a Note Off Event
        
        :param int channel: the MIDI Channel
        :param int noteNumber: the note number, range from 0-127
        :param int velocity: the note velocity, range 0-127
        :param float timeOff: the note time off, in seconds

    .. py:method:: addControlChange(self, channel: int, controlNumber: int, controlValue: int, time: float) -> None
        
        add a control change value
        automatically checks if number has been added

        :param int control_number: the control change number
        :param int channel: MIDI channel number
        :param int value: value of the control change
        :param float time: time value (in seconds)
        
    .. py:method:: addPitchwheel(self, channel: int, value: float, time: float) -> None
            
        add a pitchwheel event

        :param int channel: the MIDI channel number
        :param float value: value of the pitch wheel TODO range
        :param float time: time value (in seconds)


    .. py:method:: addAftertouch(self, channel: int, noteNumber: int, value: int, time: float) -> None
            
        add a aftertouch event

        :param int channel: the MIDI channel number
        :param float value: value of the aftertouch, TODO range
        :param float time: time value (in seconds)
        
    .. py:method:: _isEmpty(self) -> bool
            
        checks if the :class:`MIDITrack` is empty
        
        :return: True if empty, False if not
    
    .. py:method:: allUsedNotes(self) -> list
            
        returns a list of all used notes in a :class:`MIDITrack`
        
        :return: a list of all used notes

.. py:class:: MIDIFile
    
    .. py:method:: __init__(self, midiFile: str)

        open file and store it as data in lists

        tracks with channels and track names, timesOn and off information

        for each track, velocity and MIDI CC info for each track, etc


        :param str midiFile: :class:`MIDIFile` path

    .. py:method:: getMIDITracks(self) -> list
            
        returns a list of all :class:`MIDITrack` objects in the :class:`MIDIFile`
        
        :return: a list of all :class:`MIDITrack` objects
    
    .. py:method:: _parseMIDI(self, file: str) -> list
        
        helper method that takes a MIDI file (instrumentType 0 and 1) and returns a list of :class:`MIDITrack` objects

        :param midFile: MIDI file
        :return: list of MIDITracks
        :rtype: list

    .. py:method:: findTrack(self, name) -> MIDITrack

        Finds the track with a specified name

        :param str name: The name of the track to be returned
        :return list: The track with the specified name

    .. py:method:: listTrackNames(self) -> list
            
        Returns a list of all track names in the :class:`MIDIFile`
        
        :return: a list of all track names
    

```
