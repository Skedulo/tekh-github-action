# tekh github action

[tekh](https://github.com/Skedulo/tekh) is a tool to maintain terraform modules
that configure kubernetes applications using a combination of TErraform,
Kustomize and Helm

This action updates a tekh repository to latest version

## Inputs

* `chart` *Required* The name of the helm chart to use
* `url` *Required* The url of the helm repository containing the chart
* `name` *Required* The name of the application
* `namespace` *Required* The namespace in which to install the application
* `values` - path to a values file to use - defaults to none
* `additional` - additional arguments to pass to helm - defaults to none
* `update_documentation` - whether to update the documentation - defaults to false
* `documentation_file` - file to update - defaults to README.md

## Outputs

## `version`

The version of helm after running tekh

## `changed`

Whether the version has changed

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
