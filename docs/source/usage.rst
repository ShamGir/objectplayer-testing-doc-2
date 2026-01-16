Usage
=====

.. _installation:

Installation
------------

Install it with Sham Gir help:

.. code-block:: console

   (.venv) $ install objectplayer

Usage first
----------------

Once it is installed then,
you can use the ``eso.tranfer()`` function:

.. autofunction:: eso.tranfer()

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`system.get_random_ingredients`
will raise an exception.

.. autoexception:: system.InvalidKindError

For example:

>>> import system
>>> system.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

