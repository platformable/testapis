# How to create a new Document
Documents are .md files hosted on a repository

### To create a new document follow this steps:

1.- Click on Catalog -> Software

2.- Click on Create Button (top right)

3.- Follow instructions

# How to add a Document to existing component

Documents needs to have a special file structure as described below:

```
├── README.md
├── catalog-info.yaml
├── docs
│   └── index.md
├── mkdocs.yml
└── src
    └── // The code of your component
```

### Add the mkdocs configuration file
Create a file called mkdocs.yml in the root of a component you want to document in Backstage. Inside that YAML file, add the following content, replacing {component-name} with the name of your component.
```
site_name: '{component-name}'

plugins:
  - techdocs-core
# example navigation  
nav:
  - Introduction: index.md
```

### Update the YAML metadata
Use the catalog-info.yaml file of our component to tell Backstage where to find the documentation.
Add the backstage.io/techdocs-ref annotation to the list of annotations.

```
annotations:
  backstage.io/techdocs-ref: dir:.
  
```

If your docs are located elsewhere, you must explicitly point to them like this:

```
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: sample-service
  description: # ...
  annotations:
    backstage.io/techdocs-ref: url:https://github.com/your-org/your-repo/tree/main
spec:
  type: service
  owner: engineering
  lifecycle: experimental

```

⚠️ The GitHub URL must be prefixed with url: or the documentation will not render in Backstage.

