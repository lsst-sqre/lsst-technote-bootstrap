{{ "#" * (cookiecutter.title|length + cookiecutter.series|length + cookiecutter.serial_number|length + 2) }}
{{ cookiecutter.series }}-{{ cookiecutter.serial_number }} {{ cookiecutter.title }}
{{ "#" * (cookiecutter.title|length + cookiecutter.series|length + cookiecutter.serial_number|length + 2) }}

{{ cookiecutter.description }}

View this technote at {{ cookiecutter.url }}

{% if cookiecutter.docushare_url|length > 0 %}
   An authoritative version of this document is also available in LSST's Docushare: {{ cookiecutter.docushare_url }}
   {{ cookiecutter.docushare_url|length }}
{% endif %}

..
  Uncomment this section and modify the DOI strings to include a Zenodo DOI badge in the README
  .. image:: https://zenodo.org/badge/doi/10.5281/zenodo.#####.svg
     :target: http://dx.doi.org/10.5281/zenodo.#####

Build this technical note
=========================

You can clone this repository and build the technote locally with `Sphinx`_

.. code-block:: bash

   git clone https://github.com/{{ cookiecutter.github_namespace }}
   cd {{ cookiecutter.repo_name }}
   pip install -r requirements.txt
   make html

The built technote is located at ``_build/html/index.html``.

Editing this technical note
===========================

You can edit the ``index.rst`` file, which is a reStructuredText document.
A good primer on reStructuredText is available at http://docs.lsst.codes/en/latest/development/docs/rst_styleguide.html

Remember that images and other types of assets should be stored in the ``_static/`` directory of this repository.
See ``_static/README.rst`` for more information.

The published technote at {{ cookiecutter.url }} will be automatically rebuilt whenever you push your changes to the ``master`` branch on `GitHub <https://github.com/{{ cookiecutter.github_namespace }}>`_.

Updating metadata
=================

This technote's metadata is maintained in ``metadata.yaml``.
In this metadata you can edit the technote's title, authors, publication date, etc..
``metadata.yaml`` is self-documenting with inline comments.

****

Copyright {{ cookiecutter.copyright_year }} {{ cookiecutter.copyright_holder }}

This work is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/.

.. _Sphinx: http://sphinx-doc.org
