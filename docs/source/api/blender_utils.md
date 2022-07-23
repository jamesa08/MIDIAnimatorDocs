# Blender Specific Utilities

Any utilities pertaining to Blender will be here.

To import all utilities into your code:
```python
from MIDIAnimator.utils.blender import *
```

```{eval-rst}
.. py:function:: shapeKeysFromObject(obj):

    Gets shape keys  (:class:`bpy.types.ShapeKey`) from an object (:class:`bpy.types.Object`).

    :param obj: the Blender object
    :type obj: :class:`bpy.types.Object`

    :return: returns a tuple, first element being a list of the shape keys and second element being the reference key. If the object does not have any shape keys, it will return :class:`([], None)`.
    :rtype: `tuple`

.. py:function:: FCurvesFromObject(obj):

    Gets FCurves (:class:`bpy.types.FCurve`) from an object (:class:`bpy.types.Object`).

    :param obj: the Blender object
    :type obj: :class:`bpy.types.Object`

    :return: a list of :class:`bpy.types.FCurve` objects. If the object does not have FCurves, it will return an empty list.
    :rtype: `list`

.. py:function:: shapeKeysFCurvesFromObject(obj):

    Gets shape key (:class:`bpy.types.ShapeKey`) FCurves from a object (:class:`bpy.types.Object`).

    :param obj: the Blender object
    :type obj: :class:`bpy.types.Object`

    :return: a list of :class:`bpy.types.FCurve` objects. If the object does not have FCurves, it will return an empty list.
    :rtype: `list`

.. py:function:: cleanKeyframes(obj, channels: Set={"all_channels"}):

    Removes all FCurves from an object (:class:`bpy.types.Object`) unless specified by ``channels``.

    :param obj: the Blender object
    :type obj: :class:`bpy.types.Object`
    :param channels: the channels to keep. If ``"all_channels"`` is specified, all FCurve channels will be kept. If ``"all_channels"`` is not specified, only the channels specified will be kept.

    :rtype: `None`

.. py:function:: secToFrames(sec):

    Converts seconds to frames with the current context of the Blender scene (:class:`bpy.types.Scene`).

    :param float sec: time (in seconds)
    :return: the number of frames
    :rtype: float

.. py:function:: framesToSec(frames):

    Converts frames to seconds with the current context of the Blender scene (:class:`bpy.types.Scene`).

    :param float frames: time (in frames)
    :return: the number of seconds
    :rtype: float

.. py:function:: getExactFps():

    Gets the exact FPS (decimal) of the current Blender scene (:class:`bpy.types.Scene`).

    :return: the FPS
    :rtype: float

.. py:function:: cleanCollection(col: bpy.types.Collection, refObject: bpy.types.Object=None):

    Cleans/removes a collection of old objects (to be reanimated)

    :param: col: the collection to clean
    :param refObject: the reference object that should not be deleted. If not specified, all objects will be deleted.
    :rtype: None

.. py:function:: setKeyframeInterpolation(obj: bpy.types.Object, interpolation: str, data_path=None):

    Sets the interpolation of the last keyframe on an object (:class:`bpy.types.Object`).

    :param obj: the object to set the interpolation on
    :param interpolation: the interpolation to set. Can be one of the following: ``'CONSTANT'``, ``'LINEAR'``, ``'BEZIER'``, ``'SINE'``, ``'QUAD'``, ``'CUBIC'``, ``'QUART'``, ``'QUINT'``, ``'EXPO'``, ``'CIRC'``, ``'BACK'``, ``'BOUNCE'``, ``'ELASTIC'``.
   
    .. seealso:: `Blender Interpolation descriptions <https://docs.blender.org/api/current/bpy.types.Keyframe.html#bpy.types.Keyframe.interpolation>`__

    :param data_path: the data path to set the interpolation on. If not specified, the interpolation will be set on all FCurve channels.
    :rtype: None

.. py:function:: setKeyframeHandleType(obj: bpy.types.Object, handleType, data_path=None):

    Sets the handle type of the last keyframe on an object (:class:`bpy.types.Object`).

    :param obj: the object to set the interpolation on
    :param handleType: the handle type to set. Can be one of the following: ``'FREE'``, ``'ALIGNED'``, ``'VECTOR'``, ``'AUTO'``, ``'AUTO_CLAMPED'``.
    
    .. seealso:: `Blender Handle Type descriptions <https://docs.blender.org/api/current/bpy.types.Keyframe.html#bpy.types.Keyframe.handle_left_type>`__

    :param data_path: the data path to set the handle type on. If not specified, the handle type will be set on all FCurve channels.
    :rtype: None

.. py:function:: deleteMarkers(name: str):

    Deletes markers with the specified name in the current scene.

    :param name str: the name of the markers to delete
    :rtype: None

.. py:function:: distanceFromVectors(point1: Vector, point2: Vector):

    Calculates the distance between two points.

    :param point1: the first point
    :type point1: :class:`mathutils.Vector`
    :param point2: the second point
    :type point2: :class:`mathutils.Vector`
    :return: the distance (in Blender units, default is meters)
    :rtype: float

.. py:function:: velocityFromVectors(point1: Vector, point2: Vector, frames: float):

    Calculates the velocity from 2 vectors given a time (in frames).

    :param point1: the first point
    :type point1: :class:`mathutils.Vector`
    :param point2: the second point
    :type point2: :class:`mathutils.Vector`
    :param frames: the time in frames
    :type frames: float
    :return: the velocity (in Blender units, default is meters/second)
    :rtype: float

.. py:function:: timeFromVectors(point1: Vector, point2: Vector, velocity: float):

    Calculates the time needed for a specified velocity from 2 vectors.

    :param point1: the first point
    :type point1: :class:`mathutils.Vector`
    :param point2: the second point
    :type point2: :class:`mathutils.Vector`
    :param velocity: the velocity (in Blender units, default is meters/second)
    :type velocity: float
    :return: the time (in seconds)
    :rtype: float

.. py:function:: showHideObj(obj: bpy.types.Object, hide: bool, frame: int):

    Shows/hides an object (:class:`bpy.types.Object`) at a specified frame & writes a keyframe.

    :param obj: the object to show/hide
    :type obj: :class:`bpy.types.Object`
    :param hide: if ``True``, the object will be hidden. If ``False``, the object will be shown.
    :type hide: bool
    :param frame: the frame to show/hide the object at
    :type frame: int
    :rtype: None

.. py:function:: worldBoundingBox(obj: bpy.types.Object):

    Returns the corners of the bounding box of an object (:class:`bpy.types.Object`) in world coordinates.
    
    :param obj: the object to get the bounding box of
    :type obj: :class:`bpy.types.Object`

    :return: the corners of the bounding box
    :rtype: list of :class:`mathutils.Vector`

.. py:function:: objectsOverlap(obj1: bpy.types.Object, obj2: bpy.types.Object) -> bool:

    Returns whether two objects overlap or not.
    
    :param obj1: the first object
    :type obj1: :class:`bpy.types.Object`
    
    :param obj2: the second object
    :type obj2: :class:`bpy.types.Object`
    
    :return: ``True`` if the objects overlap, ``False`` otherwise
    :rtype: bool

```