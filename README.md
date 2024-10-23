# tekh github action

[tekh](https://github.com/Skedulo/tekh) is a tool to maintain terraform modules
that configure kubernetes applications using a combination of TErraform,
Kustomize and Helm

This action updates a tekh repository to latest version

## Inputs

* `chart` *Required* The name of the helm chart to use
* `name` *Required* The name of the application
* `namespace` *Required* The namespace in which to install the application
* `url` The url of the helm repository containing the chart
* `values` - path to a values file to use - defaults to none
* `version` - version of chart to use - defaults to none (i.e. latest)
* `additional` - additional arguments to pass to helm - defaults to none
* `ignore` - comma-separated list of words to ignore when considering whether
  a repo has changed. For example, helm.sh/chart,checksum/ to ignore
  non-functional chart version bumps - defaults to none
* `update_documentation` - whether to update the documentation - defaults to false
* `documentation_file` - file to update - defaults to README.md
* `working_directory` - path in which to run tekh - defaults to /github/workspace
* `version_label` - label to look at to determine chart version - defaults to
  `helm.sh/chart`
* `app_version_label` - label to look at to determine app version - defaults to
  `app.kubernetes.io/version`

## Outputs

## `version`

The version of helm after running tekh

## `changed`

Whether the version has changed

## `app_version`
The version of the application after running tekh

## Example usage

```
uses: Skedulo/tekh-action@v1
with:
  chart: karpenter/karpenter
  url: https://charts.karpenter.sh
  name: karpenter
  namespace: karpenter
  values: values.yaml
  additional: -a policy/v1
  update_documentation: true
```
