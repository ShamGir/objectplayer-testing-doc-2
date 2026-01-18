Quick Start
===========

Get up and running with ObjectPlayer in just a few minutes.

Your First Script
-----------------

Create a new Python file called ``my_first_script.py``:

.. code-block:: python

   from objectplayer import Player, Scene

   # Initialize the player
   player = Player()

   # Create a scene
   scene = Scene(name="My First Scene")
   scene.add_object("cube", position=(0, 0, 0))
   scene.add_object("sphere", position=(2, 0, 0))

   # Play the scene
   player.load(scene)
   player.play()

Run the script:

.. code-block:: console

   $ python my_first_script.py

Working with Objects
--------------------

ObjectPlayer supports various 3D primitives:

.. code-block:: python

   from objectplayer import Scene

   scene = Scene()

   # Add basic shapes
   scene.add_object("cube", size=1.0, color="red")
   scene.add_object("sphere", radius=0.5, color="blue")
   scene.add_object("cylinder", height=2.0, radius=0.3)
   scene.add_object("plane", width=10, height=10)

Transformations
~~~~~~~~~~~~~~~

Apply transformations to objects:

.. code-block:: python

   obj = scene.add_object("cube")

   # Position
   obj.set_position(x=1.0, y=2.0, z=3.0)

   # Rotation (in degrees)
   obj.set_rotation(x=45, y=0, z=90)

   # Scale
   obj.set_scale(x=2.0, y=2.0, z=2.0)

Animation Basics
----------------

Create simple animations:

.. code-block:: python

   from objectplayer import Animation, Keyframe

   # Create an animation
   anim = Animation(duration=5.0)

   # Add keyframes
   anim.add_keyframe(Keyframe(time=0, position=(0, 0, 0)))
   anim.add_keyframe(Keyframe(time=2.5, position=(5, 3, 0)))
   anim.add_keyframe(Keyframe(time=5.0, position=(0, 0, 0)))

   # Apply to object
   obj.add_animation(anim)

Exporting Your Work
-------------------

Export scenes to various formats:

.. code-block:: python

   # Export to image
   scene.export("output.png", width=1920, height=1080)

   # Export to video
   player.export_video("animation.mp4", fps=30)

   # Export scene data
   scene.save("my_scene.json")

Next Steps
----------

- Read the full :doc:`usage` guide
- Explore the :doc:`api` reference
- Check :doc:`configuration` options
- See :doc:`examples` for more complex scenarios
