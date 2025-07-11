# NimsforestFolders

Generic folder structure creation tool for the Nimsforest ecosystem.

## Purpose

Creates folder structures from JSON templates using jq for parsing. Designed to be reusable across nimsforest components.

## Quick Start

```bash
# Check system and view usage
make -f nimsforestfolders/MAKEFILE.nimsforestfolders nimsforestfolders-hello

# Auto-add to your project's main Makefile
make -f nimsforestfolders/MAKEFILE.nimsforestfolders nimsforestfolders-addtomainmake
```

## Usage

```bash
# Include in your Makefile (auto-added by addtomainmake command)
-include nimsforestfolders/MAKEFILE.nimsforestfolders

# Create folders from JSON template
make nimsforestfolders-create-folders \
  JSON_FILE=path/to/structure.json \
  BASE_PATH=output/directory

# Validate existing structure against template
make nimsforestfolders-lint \
  JSON_FILE=path/to/structure.json \
  BASE_PATH=existing/directory
```

## Examples

```bash
# Create organizational structure
make nimsforestfolders-create-folders \
  JSON_FILE=nimsforestfolders/docs/templates/organization-structure.json \
  BASE_PATH=./docs/organization

# Validate existing structure
make nimsforestfolders-lint \
  JSON_FILE=nimsforestfolders/docs/templates/organization-structure.json \
  BASE_PATH=./docs/organization
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
git submodule add https://github.com/nimsforest/nimsforestfolders.git tools/nimsforestfolders
```