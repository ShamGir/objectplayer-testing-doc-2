Changelog
=========

All notable changes to ObjectPlayer are documented here.

This project adheres to `Semantic Versioning <https://semver.org/>`_.

Version 2.1.0 (2025-01-15)
--------------------------

**Added**

- New ``ParticleEmitter`` class for particle effects
- Support for Vulkan rendering backend
- ``Scene.export_video()`` method for animation export
- Bezier curve interpolation for animations
- Physics simulation with collision detection

**Changed**

- Improved OpenGL shader compilation performance by 40%
- Updated minimum Python version to 3.8
- Refactored ``Animation`` API for better usability

**Fixed**

- Memory leak when loading large textures
- Crash on Windows when using multiple monitors
- Incorrect rotation order in ``Transform.set_rotation()``

**Deprecated**

- ``Player.render_frame()`` - use ``Player.capture()`` instead

Version 2.0.0 (2024-09-01)
--------------------------

**Breaking Changes**

- Renamed ``ObjectPlayer.init()`` to ``ObjectPlayer.setup()``
- Changed ``Scene.add()`` signature to ``Scene.add_object()``
- Configuration file format changed from INI to YAML

**Added**

- Complete rewrite of the rendering engine
- Support for PBR (Physically Based Rendering) materials
- New ``Terrain`` class for procedural landscapes
- Custom shader support with GLSL
- Real-time shadows and reflections

**Changed**

- Migrated to modern OpenGL 4.1 core profile
- Improved documentation with more examples
- Better error messages with troubleshooting hints

**Removed**

- Legacy OpenGL 2.1 support
- Deprecated ``SimpleRenderer`` class

Version 1.5.2 (2024-06-15)
--------------------------

**Fixed**

- Hot-fix for texture loading on macOS Sonoma
- Corrected UV mapping for cylinder primitives

Version 1.5.0 (2024-05-01)
--------------------------

**Added**

- Animation system with keyframe support
- Text rendering with TrueType fonts
- Screenshot capture functionality
- Support for OBJ and GLTF model formats

**Changed**

- Improved startup time by 25%
- Better handling of high-DPI displays

**Fixed**

- Z-fighting issues with overlapping objects
- Audio synchronization in animations

Version 1.0.0 (2024-01-01)
--------------------------

**Initial Release**

- Core rendering engine with OpenGL backend
- Basic 3D primitives (cube, sphere, cylinder, plane)
- Scene graph with parent-child relationships
- Camera controls (orbit, pan, zoom)
- Basic lighting (ambient, directional, point)
- Configuration file support
- Cross-platform support (Windows, macOS, Linux)

Migration Guides
----------------

Migrating from 1.x to 2.x
~~~~~~~~~~~~~~~~~~~~~~~~~

1. Update configuration files from INI to YAML format
2. Rename ``Scene.add()`` calls to ``Scene.add_object()``
3. Replace ``ObjectPlayer.init()`` with ``ObjectPlayer.setup()``
4. Update any custom shaders to GLSL 330+

See the `Migration Guide <https://github.com/objectplayer/objectplayer/wiki/Migration-Guide>`_ for detailed instructions.
