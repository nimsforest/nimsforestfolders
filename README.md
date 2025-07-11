# NimsforestFolders

Generic folder structure creation tool for the Nimsforest ecosystem.

## Purpose

Creates folder structures from JSON templates using jq for parsing. Designed to be reusable across nimsforest components.

## Usage

```bash
# Include in your Makefile
-include nimsforestfolders/MAKEFILE.nimsforestfolders

# Create folders from JSON template
make nimsforestfolders-create-folders \
  JSON_FILE=path/to/structure.json \
  BASE_PATH=output/directory \
  JSON_QUERY='jq query to extract paths'
```

## Example

```bash
make nimsforestfolders-create-folders \
  JSON_FILE=nimsforestfolders/docs/templates/organization-structure.json \
  BASE_PATH=./docs/organization \
  JSON_QUERY='.organization | to_entries[] | .key as $dept | .value | to_entries[] | .key as $func | .value[] | "\($dept)/\($func)/\(.)"'
```

## Templates

Templates are stored in `docs/templates/` and contain JSON structures that define folder hierarchies.

## Requirements

- jq (JSON processor)
- make
- bash

## Integration

Designed to be used as a Git submodule in nimsforest components:

```bash
git submodule add https://github.com/nimsforest/nimsforestfolders.git nimsforestfolders
```