# How to include Documents / md files for documentation

### Include the next code under metadata -> annotations:(mostly on catalog-info.yaml file)

```
annotations:
    backstage.io/techdocs-ref: dir:.
```

Create a “/docs” folder in template root directory and create a index.md. You can use this as starter:

```
# ${{ values.component_id }}

${{ values.description }}

## Getting started

Start writing your documentation by adding more markdown (.md) files to this
folder (/docs) or replace the content in this file.
```

Create file mkdocs.yml in root directory. And add following code:
For sidebar navigation on https://backstage.io/, see `microsite/sidebars.json`

```
site_name: ${{values.name}}
site_description: ${{values.description}}

nav:
  - Introduction: index.md

plugins:
  - techdocs-core
```


> Replace ${{values}.component_id}} and ${{values.description}} if you are adding a repository manually with your component / docs name and description