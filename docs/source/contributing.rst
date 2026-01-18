Contributing
============

We welcome contributions to ObjectPlayer! This guide will help you get started.

Code of Conduct
---------------

Please read and follow our `Code of Conduct <https://github.com/objectplayer/objectplayer/blob/main/CODE_OF_CONDUCT.md>`_.
We are committed to providing a welcoming and inclusive environment.

Getting Started
---------------

1. Fork the repository on GitHub
2. Clone your fork locally:

   .. code-block:: console

      $ git clone https://github.com/YOUR_USERNAME/objectplayer.git
      $ cd objectplayer

3. Create a virtual environment and install dependencies:

   .. code-block:: console

      $ python -m venv .venv
      $ source .venv/bin/activate
      $ pip install -e ".[dev]"

4. Create a branch for your changes:

   .. code-block:: console

      $ git checkout -b feature/your-feature-name

Development Workflow
--------------------

Running Tests
~~~~~~~~~~~~~

Run the test suite before submitting:

.. code-block:: console

   $ pytest tests/
   $ pytest tests/ -v --cov=objectplayer  # With coverage

Linting and Formatting
~~~~~~~~~~~~~~~~~~~~~~

We use ``black`` for formatting and ``ruff`` for linting:

.. code-block:: console

   $ black objectplayer/ tests/
   $ ruff check objectplayer/

Type Checking
~~~~~~~~~~~~~

Run type checks with mypy:

.. code-block:: console

   $ mypy objectplayer/

Building Documentation
~~~~~~~~~~~~~~~~~~~~~~

Build and preview documentation:

.. code-block:: console

   $ cd docs
   $ make html
   $ open build/html/index.html

Submitting Changes
------------------

1. Ensure all tests pass
2. Update documentation if needed
3. Add an entry to ``CHANGELOG.rst``
4. Commit your changes with a clear message:

   .. code-block:: console

      $ git commit -m "Add feature: description of your change"

5. Push to your fork:

   .. code-block:: console

      $ git push origin feature/your-feature-name

6. Open a Pull Request on GitHub

Pull Request Guidelines
-----------------------

- Keep PRs focused on a single feature or fix
- Include tests for new functionality
- Update documentation as needed
- Follow the existing code style
- Write clear commit messages
- Reference any related issues

Commit Message Format
~~~~~~~~~~~~~~~~~~~~~

We follow conventional commits:

.. code-block:: text

   type(scope): description

   [optional body]

   [optional footer]

Types: ``feat``, ``fix``, ``docs``, ``style``, ``refactor``, ``test``, ``chore``

Example:

.. code-block:: text

   feat(animation): add bezier curve interpolation

   Adds support for cubic bezier curves in animation keyframes.
   
   Closes #123

Reporting Issues
----------------

When reporting issues, please include:

- ObjectPlayer version (``objectplayer --version``)
- Python version
- Operating system
- Minimal code to reproduce the issue
- Expected vs actual behavior
- Any error messages or tracebacks

Feature Requests
----------------

We love hearing ideas! When proposing features:

- Check existing issues first
- Describe the use case
- Explain expected behavior
- Consider implementation complexity

Recognition
-----------

Contributors are recognized in:

- The ``CONTRIBUTORS.md`` file
- Release notes
- Our documentation

Thank you for contributing to ObjectPlayer!
