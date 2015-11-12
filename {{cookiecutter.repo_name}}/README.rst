{{ "#" * (cookiecutter.title|length + cookiecutter.series|length + cookiecutter.serial_number|length + 2) }}
{{ cookiecutter.series }}-{{ cookiecutter.serial_number }} {{ cookiecutter.title }}
{{ "#" * (cookiecutter.title|length + cookiecutter.series|length + cookiecutter.serial_number|length + 2) }}

{{ cookiecutter.description }}

View this report at {{ cookiecutter.url }}

{% if cookiecutter.docushare_url|length > 0 %}
   An authoritative version of this report is also available in LSST's Docushare: {{ cookiecutter.docushare_url }}
   {{ cookiecutter.docushare_url|length }}
{% endif %}

Build this Report
=================

You can clone this repository and build the report locally with `Sphinx`_

.. code-block:: bash

   git clone https://github.com/{{ cookiecutter.github_namespace }}
   cd {{ cookiecutter.repo_name }}
   pip install -r requirements.txt
   make html

The built report is located at ``_build/html/index.html``.

Editing this Report
===================

You can edit the ``index.rst`` file, which is a reStructuredText document.
A good primer on reStructuredText is available at http://docs.lsst.codes/en/latest/development/docs/rst_styleguide.html

Remember that images and other types of assets should be stored in the ``_static/`` directory of this repository.

The published report at {{ cookiecutter.docushare_url }} will be automatically rebuilt whenever you push your changes to the ``master`` branch on `GitHub <https://github.com/{{ cookiecutter.github_namespace }}`_.

****

Copyright {{ cookiecutter.copyright_year }} {{ cookiecutter.copyright_holder }}

This work is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/.

.. _Sphinx: http://sphinx-doc.org
