# Dashboard

The Open Data Hub Dashboard component installs a UI which 

- Shows what's installed
- Show's what's available for installation
- Links to component UIs
- Links to component documentation

For more information, visit the project [GitHub repo](https://github.com/red-hat-data-services/odh-dashboard).

### Folders
1. base: contains all the necessary yaml files to install the dashboard
2. overlays/authentication: Contains the necessary yaml files to install the
   RHODS Dashboard configured to require users to authenticate to the
   OpenShift cluster before they can access the service

##### Installation
Use the `kustomize` tool to process the manifest then apply with `oc apply` command.

```yaml
  - kustomizeConfig:
      repoRef:
        name: manifests
        path: odh-dashboard
    name: odh-dashboard
```

If you would like to configure the dashboard to require authentication:
```yaml
  - kustomizeConfig:
      overlays:
        - authentication
      repoRef:
        name: manifests
        path: odh-dashboard
    name: odh-dashboard
```