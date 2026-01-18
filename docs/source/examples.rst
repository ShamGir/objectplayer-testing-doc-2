Examples
========

This page showcases various examples demonstrating ObjectPlayer capabilities.

Basic Examples
--------------

Hello World
~~~~~~~~~~~

The simplest ObjectPlayer program:

.. code-block:: python

   from objectplayer import Player, Scene

   scene = Scene()
   scene.add_text("Hello, World!", position=(0, 0, 0), size=2)

   player = Player()
   player.load(scene)
   player.show()

Rotating Cube
~~~~~~~~~~~~~

Create an animated rotating cube:

.. code-block:: python

   from objectplayer import Player, Scene, Animation

   scene = Scene()
   cube = scene.add_object("cube", color="coral")

   # Create rotation animation
   anim = Animation(duration=4.0, loop=True)
   anim.rotate(axis="y", degrees=360)
   cube.add_animation(anim)

   Player().load(scene).play()

Intermediate Examples
---------------------

Solar System
~~~~~~~~~~~~

Create a simple solar system simulation:

.. code-block:: python

   from objectplayer import Player, Scene, Animation
   import math

   scene = Scene(background="#000011")

   # Sun
   sun = scene.add_object("sphere", radius=2, color="yellow", emission=1.0)

   # Planets
   planets = [
       {"name": "Mercury", "distance": 4, "size": 0.2, "speed": 4.0, "color": "gray"},
       {"name": "Venus", "distance": 6, "size": 0.4, "speed": 2.5, "color": "orange"},
       {"name": "Earth", "distance": 8, "size": 0.4, "speed": 1.5, "color": "blue"},
       {"name": "Mars", "distance": 10, "size": 0.3, "speed": 1.0, "color": "red"},
   ]

   for planet in planets:
       obj = scene.add_object("sphere", 
           radius=planet["size"], 
           color=planet["color"]
       )
       orbit = Animation(duration=planet["speed"], loop=True)
       orbit.orbit_around(sun, radius=planet["distance"])
       obj.add_animation(orbit)

   Player().load(scene).play()

Particle System
~~~~~~~~~~~~~~~

Create a particle fountain effect:

.. code-block:: python

   from objectplayer import Player, Scene, ParticleEmitter

   scene = Scene()

   emitter = ParticleEmitter(
       position=(0, 0, 0),
       rate=100,  # particles per second
       lifetime=3.0,
       velocity=(0, 5, 0),
       velocity_variance=1.0,
       color_start="white",
       color_end="blue",
       size_start=0.1,
       size_end=0.02,
       gravity=(0, -9.8, 0)
   )

   scene.add_emitter(emitter)
   Player().load(scene).play()

Advanced Examples
-----------------

Physics Simulation
~~~~~~~~~~~~~~~~~~

Create a physics-enabled scene with collisions:

.. code-block:: python

   from objectplayer import Player, Scene, Physics

   scene = Scene()
   physics = Physics(gravity=(0, -9.8, 0))
   scene.enable_physics(physics)

   # Ground plane
   ground = scene.add_object("plane", size=20)
   ground.physics.static = True

   # Falling objects
   for i in range(10):
       box = scene.add_object("cube", 
           position=(i * 0.5 - 2.5, 10 + i, 0),
           color="random"
       )
       box.physics.mass = 1.0
       box.physics.restitution = 0.6  # Bounciness

   Player().load(scene).play()

Procedural Terrain
~~~~~~~~~~~~~~~~~~

Generate terrain using noise:

.. code-block:: python

   from objectplayer import Player, Scene, Terrain
   import numpy as np

   scene = Scene()

   # Generate height map
   size = 100
   heightmap = np.zeros((size, size))
   for i in range(size):
       for j in range(size):
           heightmap[i, j] = np.sin(i * 0.1) * np.cos(j * 0.1) * 5

   terrain = Terrain(
       heightmap=heightmap,
       scale=(50, 10, 50),
       texture="grass"
   )
   scene.add_terrain(terrain)

   # Add water plane
   water = scene.add_object("plane", 
       size=60, 
       position=(0, -2, 0),
       material="water"
   )

   Player().load(scene).play()

Custom Shaders
~~~~~~~~~~~~~~

Apply custom GLSL shaders:

.. code-block:: python

   from objectplayer import Player, Scene, Shader

   vertex_shader = """
   #version 330
   in vec3 position;
   uniform mat4 mvp;
   void main() {
       gl_Position = mvp * vec4(position, 1.0);
   }
   """

   fragment_shader = """
   #version 330
   out vec4 fragColor;
   uniform float time;
   void main() {
       float r = sin(time) * 0.5 + 0.5;
       float g = cos(time * 0.7) * 0.5 + 0.5;
       float b = sin(time * 1.3) * 0.5 + 0.5;
       fragColor = vec4(r, g, b, 1.0);
   }
   """

   scene = Scene()
   shader = Shader(vertex=vertex_shader, fragment=fragment_shader)

   sphere = scene.add_object("sphere")
   sphere.material.shader = shader

   Player().load(scene).play()

Complete Projects
-----------------

For complete project examples, visit our GitHub repository:

- `3D Visualization Dashboard <https://github.com/objectplayer/examples/dashboard>`_
- `Game Prototype <https://github.com/objectplayer/examples/game>`_
- `Data Visualization <https://github.com/objectplayer/examples/dataviz>`_

See also: :doc:`quickstart`, :doc:`api`
