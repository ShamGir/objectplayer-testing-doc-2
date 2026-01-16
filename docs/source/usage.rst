Usage
=====

.. _installation:

Installation
------------

Install it with Sham Gir help:

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

Once it is installed then,
you can use the ``eso.tranfer()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

