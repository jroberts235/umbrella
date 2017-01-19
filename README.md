# interative_helm_deploy
The aim of this script is to provide missing functionality in helm cli but still maintain best practices for Umbrella Charts.
Instead of the Umbrella Chart creating a single deployment-name, each chart in the Umbrella will be deployed individually.  This make subsequent management much easier, as changes can be made to individual chart deployments, rather than deleting the entire stack and re-deploying.

This script parses the requirements.yaml file of an Umbrella Chart and deploys each chart individually, either from local files or it's home repository identified in the yaml. Overrides will be applied to the required charts by taking advantage of a feature in the helm that allows a file to be specified from the CLI that overrides values in in required charts at install time. The overrides file is by default, values.yaml, but can be changed.

There is an option to append the helm install output to a specified file.  This is valuable when developing, as it provides a record of deployment names for all installed components.  These name can be used to delete or upgrade charts as they are changed going forward. This file is always appended to.

You can specify `--dry-run` just as you can when running helm cli. All output is captured in the output if the `-O` has also been used.

A single chart can also be deploy from the Umbrella by specifying the chart name with the `-c` option.

Charts can also be skipped by providing a comman separated list.

##Install gem dependencies:

   `bundle install`

##Usage:

Run helmPlus from the umbrella chart directory.
It's assumed that the umbrella chart is at same filesystem level as dependency charts.


`./helmPlus --help`
