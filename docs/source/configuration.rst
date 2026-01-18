Configuration
=============

ObjectPlayer can be configured through multiple methods to suit your needs.

Configuration File
------------------

Create a ``objectplayer.yaml`` file in your project root:

.. code-block:: yaml

   # ObjectPlayer Configuration
   
   player:
     renderer: "opengl"
     resolution:
       width: 1920
       height: 1080
     antialiasing: true
     vsync: true
   
   scene:
     background_color: "#1a1a2e"
     ambient_light: 0.3
     grid_visible: true
   
   performance:
     max_fps: 60
     physics_substeps: 4
     cache_enabled: true

Environment Variables
---------------------

Override settings using environment variables:

.. list-table:: Environment Variables
   :header-rows: 1
   :widths: 30 20 50

   * - Variable
     - Default
     - Description
   * - ``OBJECTPLAYER_RENDERER``
     - ``opengl``
     - Rendering backend (opengl, vulkan, software)
   * - ``OBJECTPLAYER_DEBUG``
     - ``false``
     - Enable debug mode
   * - ``OBJECTPLAYER_LOG_LEVEL``
     - ``INFO``
     - Logging verbosity
   * - ``OBJECTPLAYER_CACHE_DIR``
     - ``~/.cache/objectplayer``
     - Cache directory location

Programmatic Configuration
--------------------------

Configure at runtime using Python:

.. code-block:: python

   from objectplayer import Config

   # Load from file
   config = Config.from_file("objectplayer.yaml")

   # Or configure programmatically
   config = Config()
   config.set("player.renderer", "vulkan")
   config.set("player.resolution.width", 2560)
   config.set("scene.background_color", "#000000")

   # Apply configuration
   player = Player(config=config)

Renderer Options
----------------

OpenGL (Default)
~~~~~~~~~~~~~~~~

Best compatibility across platforms:

.. code-block:: python

   config.set("player.renderer", "opengl")
   config.set("player.opengl_version", "4.1")

Vulkan
~~~~~~

Better performance on modern hardware:

.. code-block:: python

   config.set("player.renderer", "vulkan")
   config.set("player.vulkan_validation", False)  # Disable for production

Software
~~~~~~~~

CPU-based rendering for headless environments:

.. code-block:: python

   config.set("player.renderer", "software")
   config.set("player.software_threads", 4)

Logging Configuration
---------------------

Configure logging output:

.. code-block:: python

   import logging
   from objectplayer import setup_logging

   # Simple setup
   setup_logging(level=logging.DEBUG)

   # Advanced setup
   setup_logging(
       level=logging.INFO,
       log_file="objectplayer.log",
       format="%(asctime)s - %(name)s - %(levelname)s - %(message)s"
   )

Performance Tuning
------------------

For optimal performance:

.. code-block:: yaml

   performance:
     # Limit frame rate to reduce CPU usage
     max_fps: 60
     
     # Increase for complex physics simulations
     physics_substeps: 8
     
     # Enable caching for repeated renders
     cache_enabled: true
     cache_size_mb: 512
     
     # Use GPU acceleration when available
     gpu_compute: true

See :doc:`api` for complete configuration reference.
