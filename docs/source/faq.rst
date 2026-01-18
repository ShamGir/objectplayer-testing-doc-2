FAQ
===

Frequently asked questions about ObjectPlayer.

General Questions
-----------------

What is ObjectPlayer?
~~~~~~~~~~~~~~~~~~~~~

ObjectPlayer is a Python library for creating, manipulating, and rendering 3D scenes.
It provides an intuitive API for working with 3D objects, animations, and visualizations.

What platforms are supported?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ObjectPlayer supports:

- **Windows** 10 and later
- **macOS** 10.15 (Catalina) and later
- **Linux** (Ubuntu 20.04+, Fedora 34+, and other modern distributions)

Is ObjectPlayer free to use?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes! ObjectPlayer is open source and released under the MIT License. You can use it
for personal, commercial, and educational purposes.

Installation Questions
----------------------

Why do I get "ModuleNotFoundError: No module named 'objectplayer'"?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This usually means the package isn't installed in your current Python environment.
Try:

.. code-block:: console

   $ pip install objectplayer

If using a virtual environment, make sure it's activated:

.. code-block:: console

   $ source .venv/bin/activate  # Linux/macOS
   $ .venv\Scripts\activate     # Windows

How do I install the development version?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Install directly from GitHub:

.. code-block:: console

   $ pip install git+https://github.com/objectplayer/objectplayer.git@main

Rendering Questions
-------------------

Why is rendering slow on my machine?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Try these optimizations:

1. Lower the resolution in configuration
2. Disable anti-aliasing for testing
3. Use the software renderer for headless environments
4. Enable GPU compute if available

.. code-block:: python

   config.set("player.resolution.width", 1280)
   config.set("player.resolution.height", 720)
   config.set("player.antialiasing", False)

Can I run ObjectPlayer without a display (headless)?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes! Use the software renderer:

.. code-block:: python

   from objectplayer import Player, Config

   config = Config()
   config.set("player.renderer", "software")
   
   player = Player(config=config)

This is useful for servers and CI/CD pipelines.

Why do I see a black screen?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Common causes:

1. **No objects in scene** - Add objects with ``scene.add_object()``
2. **Camera pointing wrong direction** - Reset camera with ``scene.camera.look_at((0, 0, 0))``
3. **No lighting** - Add ambient light: ``scene.ambient_light = 0.5``
4. **Objects too far away** - Check object positions and camera distance

Animation Questions
-------------------

How do I loop an animation?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Set the ``loop`` parameter:

.. code-block:: python

   anim = Animation(duration=2.0, loop=True)

How do I chain multiple animations?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the ``then()`` method:

.. code-block:: python

   anim1 = Animation(duration=1.0).move_to((5, 0, 0))
   anim2 = Animation(duration=1.0).rotate(axis="y", degrees=90)
   
   obj.add_animation(anim1.then(anim2))

Performance Questions
---------------------

How can I improve frame rate?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Reduce polygon count in complex models
2. Use level-of-detail (LOD) for distant objects
3. Enable frustum culling
4. Batch similar objects together
5. Use texture atlases

What's the maximum number of objects supported?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This depends on hardware, but ObjectPlayer can typically handle:

- 10,000+ simple primitives on modern GPUs
- 1,000+ complex models with physics
- 100,000+ particles

Export Questions
----------------

What export formats are supported?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Images:** PNG, JPEG, BMP, TIFF

**Video:** MP4, WebM, GIF

**Scene data:** JSON, GLTF, OBJ

How do I export transparent backgrounds?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use PNG format with alpha:

.. code-block:: python

   scene.background = None  # Transparent
   scene.export("output.png", format="png", alpha=True)

Getting Help
------------

Where can I get more help?
~~~~~~~~~~~~~~~~~~~~~~~~~~

- **Documentation:** You're reading it!
- **GitHub Issues:** Report bugs and request features
- **Discussions:** Community Q&A on GitHub Discussions
- **Discord:** Real-time chat with the community

See also: :doc:`contributing`, :doc:`changelog`
