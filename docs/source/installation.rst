Installation
============

This guide covers the installation of ObjectPlayer on various platforms.

Requirements
------------

Before installing ObjectPlayer, ensure you have:

- Python 3.8 or higher
- pip (Python package manager)
- Virtual environment (recommended)

System Dependencies
~~~~~~~~~~~~~~~~~~~

On Ubuntu/Debian:

.. code-block:: console

   $ sudo apt-get install python3-dev libffi-dev

On macOS:

.. code-block:: console

   $ brew install python3 libffi

On Windows:

Download Python from `python.org <https://www.python.org/downloads/>`_ and ensure it's added to your PATH.

Installing with pip
-------------------

The recommended way to install ObjectPlayer is via pip:

.. code-block:: console

   $ pip install objectplayer

To install a specific version:

.. code-block:: console

   $ pip install objectplayer==2.1.0

Installing from Source
----------------------

Clone the repository and install in development mode:

.. code-block:: console

   $ git clone https://github.com/objectplayer/objectplayer.git
   $ cd objectplayer
   $ pip install -e .

Virtual Environment Setup
-------------------------

We recommend using a virtual environment:

.. code-block:: console

   $ python -m venv .venv
   $ source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   $ pip install objectplayer

Verifying Installation
----------------------

After installation, verify it works:

.. code-block:: python

   >>> import objectplayer
   >>> print(objectplayer.__version__)
   '2.1.0'

Troubleshooting
---------------

**ImportError: No module named objectplayer**

Ensure you've activated your virtual environment and installed the package.

**Permission denied errors**

Try installing with user permissions:

.. code-block:: console

   $ pip install --user objectplayer

For additional help, see our :doc:`faq` or open an issue on GitHub.
