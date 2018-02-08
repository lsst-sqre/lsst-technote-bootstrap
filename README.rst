#######################
lsst-technote-bootstrap
#######################

``lsst-technote-bootstrap`` is a template for LSST technical notes that are written in `reStructuredText`_, generated with `Sphinx`_, and deployed to the web with `LSST the Docs`_.

**To create an LSST technote,** use the ``@sqrbot`` command on Slack: https://developer.lsst.io/docs/technotes.html#create-a-restructuredtext-technote.

For background on the DM technote platform, see `SQR-000`_.

Running this cookiecutter for development
=========================================

**This cookiecutter project should only be invoked manually for development.**
To create and publish a technote, follow the instructions linked above.

The following instructions are for template developers.

1. Install cookiecutter
-----------------------

Install `cookiecutter`_ via:

.. code-block:: bash

   pip install cookiecutter

2. Run cookiecutter
--------------------

Start a new technote project in a convenient directory.
Run this command (verbatim):

.. code-block:: bash

   cookiecutter https://github.com/lsst-sqre/lsst-technote-bootstrap.git

(Alternatively you can ``git clone`` this repository and run cookiecutter directly on it: ``cookiecutter lsst-technote-bootstrap``).

Answer the prompts, and you'll have a brand new technote project.
`The prompts are documented below <#configuration-prompts>`_.

**Note:** If you're running cookiecutter_ with Python 3, you *might* get a ``RuntimeError``::

    RuntimeError: Click will abort further execution because Python 3 was configured to use ASCII as encoding for the environment.  Either run this under Python 2 or consult http://click.pocoo.org/python3/ for mitigation steps.

See `Cookiecutter and Python 3 <#cookiecutter-and-python-3>`_ for a solution.

Configuration prompts
=====================

This section describes the content expected by the prompts when running `cookiecutter`_ to create a new technote project.

- ``first_author``: The first author's name, formatted as "First Last". You can edit ``metadata.yaml`` to add additional authors.
- ``series``: The technote series, which can be

  - ``SQR`` for SQuaRE technical notes
  - ``DMTN`` for Data Management technical notes
  - ``SMTN`` for Simulations Group technical notes

- ``serial_number``: the serial number. Use three digits padded with zeros.
- ``title``: Title of the technote.
- ``github_org``: The GitHub organization where this technote resides, which can be

  - ``lsst-dm`` for the DM DMTN series
  - ``lsst-sqre`` for the SQuaRE SQR series
  - ``lsst-sims`` for the Simulations Group's SMTN series

- ``github_namespace``: This is the expected GitHub URL of the technote, minus the 'github.com/' prefix. For example, ``lsst-sqre/sqr-000``.
- ``docushare_url``: The URL of the technote on Docushare, if the canonical version is stored there. If Docushare is not used, leave this field blank.
- ``description``: This should be a short, 1-2 sentence description of the technote. This description is placed just below the title in the README.
- ``copyright_year``: Should be the current year for new projects
- ``copyright_holder``: Should your institution (For example ``Association of Universities for Research in Astronomy, Inc.`` or ``University of Washington``).

Note that errors when entering `cookiecutter`_ prompts can be easily fixed by editing the ``index.rst``, ``README.rst`` and ``metadata.yaml`` files in the generated technote project.


Cookiecutter and Python 3
=========================

Depending on how your shell is set up, you may get this error when running cookiecutter_ under Python 3::

    RuntimeError: Click will abort further execution because Python 3 was configured to use ASCII as encoding for the environment.  Either run this under Python 2 or consult http://click.pocoo.org/python3/ for mitigation steps.

To solve this, you need to set your shell's *locale* to use UTF-8.
Type these lines into your shell:

.. code-block:: bash

   export LC_ALL=en_US.utf-8
   export LANG=en_US.utf-8

*This will work on macOS. Linux distributions may be different (try C.UTF-8).*

After the locale is set, re-try the cookiecutter_ command.

****

Copyright 2015-2018 Association of Universities for Research in Astronomy, Inc.

`lsst-technote-bootstrap` is open source (MIT license).

.. _SQR-000: https://sqr-000.lsst.io
.. _`LSST the Docs`: https://sqr-006.lsst.io
.. _Zenodo: http://zenodo.org
.. _reStructuredText: http://sphinx-doc.org/rest.html
.. _Sphinx: http://sphinx-doc.org
.. _cookiecutter: http://cookiecutter.rtfd.org/
