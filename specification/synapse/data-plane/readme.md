# Azure Synapse Analytics


> see https://aka.ms/autorest

This is the AutoRest configuration file for Azure Synapse Analytics.



---
## Getting Started
To build the SDK for Azure Synapse Analytics, simply [Install AutoRest](https://aka.ms/autorest/install) and in this folder, run:

> `autorest`

To see additional help and options, run:

> `autorest --help`
---

## Configuration



### Basic Information
These are the global settings for the Azure Synapse Analytics API.

``` yaml
openapi-type: data-plane
tag: package-2019-11-01-preview
```

## Suppression
``` yaml
directive:
  - suppress: DefinitionsPropertiesNamesCamelCase
    reason: This would require a breaking change, and need to be consistent with the response from RP side.
    from: Microsoft.Synapse/preview/2019-11-01-preview/sparkFrontend.json
    where:
      - $.definitions.LivyStatementsResponseBody.properties.total_statements
      - $.definitions.LivyStatementOutput.properties.execution_count

  - suppress: DefinitionsPropertiesNamesCamelCase
    reason: These properties need to keep the same with jupyter notebook. Rp can't change these proeprties.
    from: Microsoft.Synapse/preview/2019-11-01-preview/adf/entityTypes/NoteBook.json
    where:
      - $.definitions.NotebookCellOutputItem.properties.execution_count
      - $.definitions.NotebookCellOutputItem.properties.output_type
      - $.definitions.NotebookCell.properties.cell_type
      - $.definitions.NotebookLanguageInfo.properties.codemirror_mode
      - $.definitions.NotebookKernelSpec.properties.display_name
      - $.definitions.NotebookMetadata.properties.language_info
      - $.definitions.NoteBook.properties.nbformat_minor
```

### Tag: package-2019-11-01-preview

These settings apply only when `--tag=package-2019-11-01-preview` is specified on the command line

``` yaml $(tag) == 'package-2019-11-01-preview'
input-file:
- Microsoft.Synapse/preview/2019-11-01-preview/monitoring.json
- Microsoft.Synapse/preview/2019-11-01-preview/sparkFrontend.json
- Microsoft.Synapse/preview/2019-11-01-preview/workspaceAcl.json
```

---
# Code Generation


## Swagger to SDK

Swagger to SDK has been intentionally disabled for this spec.

## C#

These settings apply only when `--csharp` is specified on the command line.
Please also specify `--csharp-sdks-folder=<path to "SDKs" directory of your azure-sdk-for-net clone>`.

``` yaml $(csharp)
csharp:
  azure-arm: true
  license-header: MICROSOFT_MIT_NO_VERSION
  namespace: Microsoft.Azure.Synapse
  output-folder: $(csharp-sdks-folder)/synapse/Microsoft.Azure.Synapse/src/Generated
  clear-output-folder: true
```

## TypeScript

See configuration in [readme.typescript.md](./readme.typescript.md)
## Multi-API/Profile support for AutoRest v3 generators 

AutoRest V3 generators require the use of `--tag=all-api-versions` to select api files.

This block is updated by an automatic script. Edits may be lost!

``` yaml $(tag) == 'all-api-versions' /* autogenerated */
# include the azure profile definitions from the standard location
require: $(this-folder)/../../../profiles/readme.md

# all the input files across all versions
input-file:
  - $(this-folder)/Microsoft.Synapse/preview/2019-11-01-preview/monitoring.json
  - $(this-folder)/Microsoft.Synapse/preview/2019-11-01-preview/sparkFrontend.json
  - $(this-folder)/Microsoft.Synapse/preview/2019-11-01-preview/workspaceAcl.json

```

If there are files that should not be in the `all-api-versions` set, 
uncomment the  `exclude-file` section below and add the file paths.

``` yaml $(tag) == 'all-api-versions'
#exclude-file: 
#  - $(this-folder)/Microsoft.Example/stable/2010-01-01/somefile.json
```

