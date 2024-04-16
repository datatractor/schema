<div align="center" style="padding-bottom: 1em;">
<img width="100px" align="center" src="https://avatars.githubusercontent.com/u/74017645?s=200&v=4">
</div>

# <div align="center">datatractor: schema</div>
<div align="center">

[![Documentation](https://badgen.net/badge/docs/datatractor.github.io/blue?icon=firefox)](https://datatractor.github.io/schema)
![Github status](https://badgen.net/github/checks/datatractor/schema/?icon=github)

</div>

A repository containing the [LinkML](https://linkml.io/linkml/)-based schemas backing the registry of extractors at [tractor yard](https://github.com/datatractor/yard/) and powering the reference implementation of the extractor framework at [tractor beam](https://github.com/datatractor/beam/).

This repository is a continuation of the MaRDA WG7 on Automated [Metadata Extractors](https://www.marda-alliance.org/working-group/wg7-automated-metadata-extractors/).

## Contents
The repository contains two user-facing schemas:

- ``FileType`` schema, used to specify the types of files passed to the extractors by users. The schema definition is located in [``filetype.yaml``](./schemas/filetype.yaml).

- ``Extractor`` schema, used to specify the download, installation, and usage instructions, allowing for machine execution of the defined extractor/parser code, as well as a list of ``FileTypes`` compatible with the ``Extractor``. The schema definition is located in [``extractor.yaml``](./schemas/extractor.yaml).

## Usage
### Validation
The schema definitions contained in this repository can be used to locally validate your own ``FileTypes`` and ``Extractors``. Several examples are provided for this purpose in the [``examples`` folder](./examples/).

To get started, first make sure LinkML is installed in your python environment. You may use the provided ``requirements.txt`` file for this purpose:

```
pip install -r requirements.txt
```

Then, you can check the validity of your filetype or extractor definition against the provided schemas using ``linkml-validate``. For example, to validate the provided example filetype definition in [``FileType-netcdf.yaml``](./examples/FileType-netcdf.yaml) against the ``FileType`` class from ``schemas/filetype.yaml``, run:

```
linkml-validate -s schemas/filetype.yaml -C FileType examples/FileType-netcdf.yaml
```

If successful, you should see "``✓ No problems found``" returned by ``linkml-validate``.

### Translation

The LinkML schemas provided here can be automatically translated to other formats, including JSONSchema, Python dataclasses, or Pydantic classes:

```
gen-json-schema schemas/extractor.yaml >> extractor.json
gen-python schemas/filetype.yaml >> filetype.py
gen-pydantic schemas/extractor.yaml >> extractor.py
```

The generated files can be used in downstream codes such as in the [validation function](https://github.com/datatractor/beam/blob/main/tasks.py#L33) of [datatractor beam](https://github.com/datatractor/beam).

## Contributing

Contributions are welcome. We pledge to follow the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/).

If you wish to contribute a new `FileType` or a new `Extractor` to the Registry, please open a pull request at the [datatractor yard repo](https://github.com/datatractor/yard).

If you have any suggestions, technical queries, or a feature request related to the schemas, please do not hesitate to open an issue in this repository. For general questions related to the datatractor project, please use the [datatractor schema discussion board](https://github.com/datatractor/schema/discussions).
