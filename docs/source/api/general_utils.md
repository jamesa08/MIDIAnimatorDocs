# General Utilities

To import all utilities into your code:
```python
from MIDIAnimator.utils import *
```


```{eval-rst}
.. py:function:: noteToName(nVal: int):

    Takes a MIDI note number and returns the name
    
    Example: ``noteToName(60)`` returns ``"C3"``

    :param nVal: the MIDI note number
    :type nVal: int

    :return: the name of the note
    :rtype: str

    :raises AssertionError: if ``nVal`` is not an integer

.. py:function:: nameToNote(nVal: str):

    Takes a note name and returns the MIDI note number
    
    Example: ``nameToNote("C3")`` returns ``60``
    
    :param nVal: the note name
    :type nVal: str
    
    :return: the MIDI note number
    :rtype: int

    :raises AssertionError: if ``nVal`` is not an integer


.. py:function:: convertNoteNumber(inputStr: str):

    Converts a note number string to a list.
    
    Example: ``convertNoteNumber("60, C#3, 62")`` returns ``[60, 61, 62]``
    
    :param inputStr: the note number string
    :type inputStr: str
    
    :return: a list of MIDI note numbers
    :rtype: list of integers
    
    :raises ValueError: if the input string is not a valid note number string

.. py:function:: gmProgramToName(pcNum: int):

    Takes a GM program change number and returns the name
    
    Example: ``gmProgramToName(0)`` returns ``"Acoustic Grand Piano"``
    
    :param pcNum: the GM program change number
    :type pcNum: int
    
    :return: the name of the program
    :rtype: str
    
    :raises AssertionError: if ``pcNum`` is not an integer
    :raises AssertionError: if ``pcNum`` is not in range of 0-127

.. py:function:: removeDuplicates(vals: list):
    
    Removes duplicates from a list.
    
    :param vals: the list to remove duplicates from
    :type vals: list
    
    :return: the list with duplicates removed
    :rtype: list
    
.. py:function:: rotateAroundCircle(radius, angle):
    
    Returns a point on a circle given a radius and angle.
    
    Takes a radius (x) and an angle (y) and returns it's X & Y.
    
    :param radius: the radius of the circle
    :type radius: float
    
    :param angle: the angle of the point on the circle
    :type angle: float
    
    :return: the point on the circle
    :rtype: tuple(x, y)


.. py:function:: mapRange(value, inMin, inMax, outMin, outMax):
    
    Maps a value from one specified range to another.
    
    :param value: the value to map
    :type value: float
    
    :param inMin: the minimum value of the input range
    :type inMin: float
    
    :param inMax: the maximum value of the input range
    :type inMax: float
    
    :param outMin: the minimum value of the output range
    :type outMin: float
    
    :param outMax: the maximum value of the output range
    :type outMax: float
    
    :return: the mapped value
    :rtype: float
```

<!-- .. note:: `note here` -->
