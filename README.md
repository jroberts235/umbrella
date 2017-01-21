# Umbrella

**Umbrella** is a [helm](https://github.com/kubernetes/helm) plugin. The aim of this plugin is to provide missing functionality in helm cli but still maintain best practices for umbrella charts.

Instead of the umbrella chart creating a single deployment-name, each chart in the umbrella will be deployed individually.  This make subsequent management much easier, as changes can be made to individual chart deployments, rather than deleting the entire stack and re-deploying.

**Umbrella** parses the requirements.yaml file of an umbrella chart and deploys each chart individually, either from local files or it's home repository identified in the yaml. **Umbrella** takes advantage of a feature in helm that allows a file to be specified from the CLI which overrides values in required charts. The overrides file is by default, values.yaml, but can be changed.

There is an option to append the helm install output to a specified file.  This is valuable when developing, as it provides a record of deployment names for all installed components. These name can be used to delete or upgrade charts as they are changed going forward. **Umbrella** will append helm install output to this file.

You can specify `--dry-run` just as you can when running helm cli. All output is captured in the output if the `-O` has also been used.

A single chart can also be deploy from the umbrella by specifying the chart name with the `-c` option.

Charts can also be skipped by providing a comman separated list.

## Flags

### `-c [chartname]`

Install a single chart from the requirements.yaml.

### `--dry-run`

Same as helm's `--dry-run`.

### `-o --output [filename]`

Appends `helm install` output to filename. This is useful for referencing specific charts.

### `--values [filename]`

Supply a custom `values.yaml` file.

