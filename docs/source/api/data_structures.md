# Data Structures
*found under `/MIDIAnimator/data_structures/__init__.py`*

```{eval-rst}
.. py:class:: NoteAnimator
    
    Takes ``obj``, ``fCurves``, ``_frameStartOffset``, ``_frameEndOffset`` and creates a :class:`NoteAnimator` object.
    
    .. py:attribute:: obj
    
        The object to be animated.
        
        :type: :class:`bpy.types.Object`
        
        
    .. py:attribute:: fCurves
    
        The FCurves of the object.
        
        :type: :class:`ObjectFCurves`
        
    .. py:attribute:: _frameStartOffset
    
        How many frames before a note is hit does this need to start animating
        
        :type: float
        
    .. py:attribute:: _frameEndOffset
        
        How many frames after a note is hit does it continue animating

        :type: float


.. py:class:: ObjectFCurves

    .. py:attribute:: location
        
        The 3 location FCurves of the reference object.
        
        :type: tuple of :class:`bpy.types.FCurve`
    
    .. py:attribute:: rotation
        
        The 3 rotation FCurves of the reference object.
        
        :type: tuple of :class:`bpy.types.FCurve`
    
    .. py:attribute:: material
        
        The custom property FCurves of the reference object.
        
        :type: tuple of :class:`bpy.types.FCurve`
    
    .. py:attribute:: shapeKeysDict
            
        A dictionary of the shape keys of the reference object.
        
        :type: dict of :class:`bpy.types.FCurve`, :class:`bpy.types.ShapeKey`

    .. py:attribute:: shapeKeys
            
        A list of the reference object's shape keys :class:`bpy.types.FCurve`'s.
        
        :type: tuple of :class:`bpy.types.FCurve`
    
.. py:class:: FCurveProcessor

    .. py:attribute:: obj
        
        The object to be animated.
        
        :type: :class:`bpy.types.Object`

    .. py:attribute:: locationObject
        
        The location object to be animated. 
        
        :type: Optional[ :class:`bpy.types.Object` ] 

    .. py:attribute:: fCurves
        
        The FCurves of the object.
        
        :type: :class:`ObjectFCurves`

    .. py:attribute:: location

        The location of the animated object

        :type: Vector

    .. py:attribute:: rotation

        The rotation of the animated object

        .. note:: Rotation is only supported in Euler mode.
        
        :type: Euler
    
    .. py:attribute:: material

        The custom properties of the animated object

        key= custom property name, value=int or float (the val to be keyframed)

        :type: dict
    
    .. py:attribute:: shapeKeys

        The shape keys of the animated object

        key= the "to keyframe" object's shape key's name, value= a float (the val to be keyframed)

        :type: dict
    
    .. py:method:: applyFCurve(self, delta: int):
            
        Applies the FCurves to the object.
        
        :param int delta: The relativie frame number. This is the current frame - the ``noteOn`` time in frames.
        
        :return: None
        
    .. py:method:: insertKeyframes(self, frame: int):
            
        Inserts keyframes on all FCurve channels at the given frame number.
        
        :param int frame: The absolute frame number. This will insert the keyframes at this frame.
        
        :return: None

.. py:class:: FrameRange

    This stores an object that will be moving from startFrame to endFrame

    .. py:attribute:: startFrame
        
        The start frame of this object's particular animation.
        
        :type: int

    .. py:attribute:: endFrame
        
        The end frame of this object's particular animation.
        
        :type: int

    .. py:attribute:: obj
        
        The object to be animated.
        
        :type: :class:`bpy.types.Object`

.. py:class:: CacheInstance

    This will group all objects that should be reused (such as projectiles), 
    and has methods to give you objects and return objects to and from the cache.

    .. py:method:: __init__(self, objs: List[bpy.types.Object])

        Initializes a type ``List[bpy.types.Object]`` to the cache instance.

        :param List[bpy.types.Object] objs: The objects to be cached.
        
        :return: None

    .. py:method:: getObject(self)
        
        Takes out a :class:`bpy.types.Object` from the cache. This is the method to use when you want to take an object out
        
        :return: A cached object.
        
        :rtype: :class:`bpy.types.Object`
    
    .. py:method:: returnObject(self, obj: bpy.types.Object)
        
        Returns a :class:`bpy.types.Object` to the cache. This is the method to use when you are done with the object.
        
        :param obj: The object to be returned to the cache.
        :type obj: :class:`bpy.types.Object`
        
        :return: None

```
