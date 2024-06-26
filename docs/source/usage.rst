Usage of Datatractor Schema
===========================

Usage example
-------------

This repository is intended to be used as a |git submodule|_ to be cloned and used by your downstream code. As an example, we may look at the |yard|_:

.. figure:: images/registry.screenshot.PNG
   :target: https://github.com/datatractor/yard
   :alt: A screenshot of the Datatractor Yard showing "schemas" as a link to another repository.

   A screenshot of |yard|. Note that ``schemas`` is a ``git submodule``, pointing to the Schema repository at a certain commit (here: |c03a732|_, corresponding to the 1.0 release).

After initializing and updating the submodule, the yaml files defining the |FileType|_ and |Extractor|_ schemas are available in the ``<submodule>/schemas/`` directory.

Validation
----------
The schema definitions contained in this repository can be used to locally validate your own :class:`FileTypes` and :class:`Extractors`. Several examples are provided for this purpose in the |examples|_ folder.

To get started, first make sure |LinkML|_ is installed in your python environment:

.. code-block:: bash

    pip install linkml~=1.3


Then, you can check the validity of your filetype or extractor definition against the provided schemas using ``linkml-validate``. For example, to validate the provided example |FileType|_ definition in |netcdf|_ against the |FileType|_ schema, run:

.. code-block:: bash

    linkml-validate -s <submodule>/schemas/filetype.yml -C FileType <submodule>/examples/filetype/netcdf.yml


If successful, you should see ``✓ No problems found`` returned by ``linkml-validate``.

Translation
-----------

The |LinkML|_ schemas provided here can be automatically translated to other formats, including ``JSONSchema``, Python ``dataclasses``, or |Pydantic|_ classes:

.. code-block:: bash

    gen-json-schema <submodule>/schemas/filetype.yml >> filetype.json
    gen-python <submodule>/schemas/filetype.yml >> filetype.py
    gen-pydantic <submodule>/schemas/filetype.yml >> filetype.py

The generated files are intended to be used in downstream codes such as in the `validation function <https://github.com/datatractor/yard/blob/main/tasks.py#L33>`_ of the |yard|_.


.. |git submodule| replace:: ``git submodule``

.. _git submodule: https://git-scm.com/book/en/v2/Git-Tools-Submodules

.. |yard| replace:: Datatractor Yard

.. _yard: https://github.com/datatractor/yard

.. |c03a732| replace:: ``c03a732``

.. _c03a732: https://github.com/datatractor/yard/commit/c03a732a217312398fd470f491271670c9cecb66

.. |LinkML| replace:: :mod:`LinkML`

.. _LinkML: https://linkml.io/linkml/

.. |FileType| replace:: :class:`FileType`

.. _FileType: datatractor_schema/FileType.html#class-filetype

.. |Extractor| replace:: :class:`Extractor`

.. _Extractor: datatractor_schema/Extractor.html#class-extractor

.. |examples| replace:: ``examples``

.. _examples: https://github.com/datatractor/schema/tree/main/examples

.. |netcdf| replace:: :mod:`netcdf.yml`

.. _netcdf: https://raw.githubusercontent.com/marda-alliance/metadata_extractors_schema/main/examples/filetype/netcdf.yml

.. |Pydantic| replace:: :class:`Pydantic`

.. _pydantic: https://docs.pydantic.dev/latest/
