#######################
lsst-technote-bootstrap
#######################

Write technotes that are native to the web
==========================================

``lsst-technote-bootstrap`` is a template for LSST technical notes that are written in `reStructuredText`_, generated with `Sphinx`_, and deployed to the web with `Read the Docs`_.

For background on the DM technote platform, see `SQR-000 <http://sqr-000.lsst.io>`_.

.. _reStructuredText: http://sphinx-doc.org/rest.html
.. _Sphinx: http://sphinx-doc.org
.. _Read the Docs: http://readthedocs.org

Quick Start
===========

1. Install cookiecutter
-----------------------

We use `cookiecutter`_ to help you create a new technote.
Install cookiecutter via:

.. code-block:: bash

   pip install cookiecutter

.. _cookiecutter: http://cookiecutter.rtfd.org/

2. Create a technote
--------------------

Start a new technote project in a convenient directory.
Run this command (verbatim):

.. code-block:: bash

   cookiecutter https://github.com/lsst-sqre/lsst-technote-bootstrap.git

(Alternatively you can ``git clone`` this repository and run cookiecutter directly on it: ``cookiecutter lsst-technote-bootstrap``).

Answer the prompts, and you'll have a brand new technote project.
The prompts are documented below in this README.

``cd`` into the technote's directory and initialize git:

.. code-block:: bash

   cd {{repo_name}}
   git init .
   git add *
   git commit -m "Init technote"

3. Customize the technote's Metadata and README
------------------------------------------------

We maintain technote metadata (such as authors, title, etc.) in the ``metadata.yaml`` file contained in the technote's repository.

Edit the metadata to correct any errors made in the cookiecutter prompts, or to add additional authors.

You can also edit the README.rst to give additional cues to readers/authors viewing the technote on GitHub.

4. Write the Docs
-----------------

Write the technote in ``index.rst``.
The markup language of DM is `reStructuredText`_.
We've written a page on writing reStructuredText for DM that may help you get started: http://docs.lsst.codes/en/latest/development/docs/rst_styleguide.html

To preview your technote, install python dependencies via

.. code-block:: bash

   pip install -r requirements.txt

once, and run

.. code-block:: bash

   make html

to generate the technote webpage locally at ``_build/html/index.html``.

5. Push to GitHub
-----------------

The technote should be published on GitHub.
Which organization you place the technote in depends on the document's series.

SQuaRE technical notes (SQR series) go in https://github.com/lsst-sqre.
DM technical notes (DMTN series) go in https://github.com/lsst-dm.
Official, change-controlled documents (LDM, LSE, etc.) go in the main https://github.com/lsst organization.

Ensure that the ``github_namespace`` you provided at the ``cookiecutter`` prompt matches the technote's name and organization on GitHub.

The repo's GitHub summary line should correspond to the technote's title and the homepage should be the URL of the published technote.

6. Publish with Read the Docs
-----------------------------

LSST technotes are continuously distributed (published) to the web using http://readthedocs.org.
To publish to `Read the Docs`_, let Jonathan Sick (jsick at lsst org) know, and he will

1. Create a `Read the Docs`_ project, and
2. Create an ``lsst.io`` url for the technote.
3. Create a Travis CI test for Sphinx builds

This is a one-time step for each technote.
Whenever you push changes to your ``master`` branch on GitHub, the generated technote on `Read the Docs`_ will be automatically updated.

We *do* plan to make this even easier by automatically provisioning Read the Docs projects via an API.

7. Get a DOI with Zenodo
------------------------

A Digital Object Identifier (DOI) allows your technote to be cited in literature.
Zenodo_ is an archive that provides DOIs.

To connect your technote's GitHub repo to Zenodo_, follow the instructions at https://guides.github.com/activities/citable-code/.

When following the `Creating a new Release`_ section of GitHub's instructions, use semvar (e.g., ``v1.0``) for both the release tag *and* title. 
The release description can be something as simple as 'v1.0 release of SQR-001: Git LFS Architecture Note'.

.. _Creating a New Release: https://guides.github.com/activities/citable-code/#create

When following the `Minting a DOI`_ section of GitHub's instructions, you'll add metadata about the technote.
Here is some guidance on what metadata to add:

.. _Minting a DOI: https://guides.github.com/activities/citable-code/#finishing

- **Types(s) of Files**: 'Publication'.
- **Publication type**: 'Technical note'.
- **Publication date**: Date of publication, or today.
- **Title**: Use the 'Series-Serial: tag format'. E.g. 'SQR-001 v1.0'.
- **Authors**: List all authors (matching ``metadata.yaml``) and their affiliations. You may need to manually add authors that aren't in the git history.
- **Keywords**: Add the 'lsst' keyword. Also add a keyword for the technote series, such as 'lsst-sqr' for 'SQR-NNN' technotes.
- **License**: 'Creative Commons Attribution'
- **Access Rights**: 'Open Access'
- **Communities**: 'Large Synoptic Survey Telescope Data Management'

Note that the 'Large Synoptic Survey Telescope Data Management' collection (`lsst-dm`_) organizes DM technotes to provide additional visibility.

.. _lsst-dm: https://zenodo.org/collection/user-lsst-dm

Once your metadata is prepared, you can **Submit** the technote and generate a DOI and object page on Zenodo.

In your ``README.rst``, uncomment the markup for the DOI badge (updating it with your technote's DOI), and add the DOI to ``metadata.yaml``.

.. _Zenodo: http://zenodo.org


.. _config-prompts:

Configuration Prompts
=====================

This section describes the content expected by the prompts when running `cookiecutter`_ to create a new technote project.

- ``first_author``: The first author's name, formatted as "First Last". You can edit ``metadata.yaml`` to add additional authors.
- ``series``: The technote series, which can be

  - ``SQR`` for SQuaRE technical notes
  - ``DMTN`` for Data Management technical notes

- ``serial_number``: the serial number. Use three digits padded with zeros.
- ``title``: Title of the technote.
- ``github_org``: The GitHub organization where this technote resides, which can be

  - ``lsst`` for change-controlled documents
  - ``lsst-dm`` for the DM DMTN series
  - ``lsst-sqre`` for the SQuaRE SQR series

- ``github_namespace``: This is the expected GitHub URL of the technote, minus the 'github.com/' prefix. For example, ``lsst-sqre/sqr-000``.
- ``docushare_url``: The URL of the technote on Docushare, if the canonical version is stored there. If Docushare is not used, leave this field blank.
- ``description``: This should be a short, 1-2 sentence description of the technote. This description is placed just below the title in the README.
- ``copyright_year``: Should be the current year for new projects
- ``copyright_holder``: Should be ``AURA/LSST`` for technotes made by DM employees.

Note that errors when entering `cookiecutter`_ prompts can be easily fixed by editing the ``index.rst``, ``README.rst`` and ``metadata.yaml`` files in the generated technote project.

****

Copyright 2015 AURA/LSST

`lsst-technote-bootstrap` is open source (MIT license).
