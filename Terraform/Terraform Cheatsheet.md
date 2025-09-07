---
Title: Terraform Cheatsheet
date: 2025-02-25
tags:
  - terraform
  - cheatsheets
---
### Main Commands

| Command              | Description                                          |
| -------------------- | ---------------------------------------------------- |
| `terraform init`     | To initialize the Project                            |
| `terraform validate` | Check whether the configuration is valid             |
| `terraform plan`     | Shows which changes will takes place after apply     |
| `terraform apply`    | Incorporate changes/ Update or create infrastructure |
| `terraform destroy`  | Destroy previously created infrastructure            |

### Other Commands

| Command                              | Description                                                                                                    |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| `terraform show`                     | Show the current state or a saved plan                                                                         |
| `terraform show <path to statefile>` | Read a specific state file                                                                                     |
| `terraform test`                     | Execute integration tests for Terraform modules                                                                |
|                                      | Reformat your configuration in the standard style                                                              |
| `terraform providers`                | Show the providers required for this configuration                                                             |
| `terraform version`                  | Show the current version of your Terraform and notifies you if there is a newer version available for download |

### Format your terraform code

| Command                     | Description                                                                                                                                                                                  |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `terraform fmt`             | Format your Terraform configuration files using the HCL language standard.                                                                                                                   |
| `terraform fmt --recursive` | Also format files in subdirectories                                                                                                                                                          |
| `terraform fmt --diff`      | Display differences between original configuration files and formatting changes                                                                                                              |
| `terraform fmt --check`     | Ensure the configuration files are formatted correctly, if not the exit status will be non-zero. If files are formatted correctly, the exit status will be zero. (Useful in CI/CD pipelines) |

### Initialize your directory

| Command                                | Description                                                                                                                                |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `terraform init`                       | Prepare the working directory to work with terraform, performs Backend Initialization, Child Module Installation, and Plugin Installation. |
| `terraform init -get-plugins=false`    | Initialize the working directory for project but dont download plugins                                                                     |
| `terraform init -lock=false`           | Initialize the working directory, don’t hold a state lock during backend migration.                                                        |
| `terraform init -input=false`          | Initialize the working directory, and disable interactive prompts.                                                                         |
| `terraform init -migrate-state`        | Reconfigure a backend, and attempt to migrate any existing state.                                                                          |
| `terraform init -verify-plugins=false` | Initialize the working directory, do not verify plugins for Hashicorp signature                                                            |

### Download and Installs the modules

| Command                 | Description                                                 |
| ----------------------- | ----------------------------------------------------------- |
| `terraform get`         | Download and installs modules needed for the configuration. |
| `terraform get -update` | Check for updates of already installed modules.             |

### Validate your Terraform Code

| Command                    | Description                                                    |
| -------------------------- | -------------------------------------------------------------- |
| `terraform validate`       | Validate the configuration files in your directory             |
| `terraform validate -json` | To see easier the number of errors and warnings that you have. |

### Plan Your Infrastructure

| Command                      | Description                                                                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `terraform plan`             | Plan will generate an execution plan, showing you what actions will be taken without actually performing the planned actions. |
| `terraform plan -out=<path>` | Save the plan file to a given path. Can then be passed to the `terraform apply` command.                                      |
| `terraform plan -destroy`    | Create a plan to destroy all objects rather than the usual actions                                                            |

### Deploy Your Infrastructure

| Command                                      | Description                                                                                                                                                    |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `terraform apply`                            | Create or update infrastructure depending on the configuration files                                                                                           |
| `terraform apply -auto-approve`              | Apply changes without having to interactively type ‘yes’ to the plan. Useful in automation CI/CD pipelines.                                                    |
| `terraform apply <planfilename>`             | Provide the file generated using the `terraform plan -out` command. If provided, Terraform will take the actions in the plan without any confirmation prompts. |
| `terraform apply -lock=false`                | Do not hold a state lock during the Terraform apply operation. Use with caution if other engineers might run concurrent commands against the same workspace.   |
| `terraform apply -parallelism=<n>`           | Specify the number of operations run in parallel.                                                                                                              |
| `terraform apply -var="environment=dev`      | Pass in a variable value.                                                                                                                                      |
| `terraform apply -var-file="varfile.tfvars"` | Pass in variables contained in a file.                                                                                                                         |
| `terraform apply -target=”module.appgw.0"`   | Apply changes only to the targeted resource.                                                                                                                   |

### Destroy your Infrastructure

| Command                                                      | Description                                                 |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| `terraform destroy`                                          | Destroy the Infrastructure managed and created by Terraform |
| `terraform destroy -target=”module.appgw.0"`                 | Destroy only the targeted resource.                         |
| `terraform destroy --auto-approve`                           | Dont ask for interactive prompt                             |
| `terraform destroy -target="module.appgw.resource[\"key\"]"` | Destroy an instance of a resource created with for_each.    |
### ‘Taint’ or ‘Untaint’ Your Resources
Use the `taint` command to mark a resource as not fully functional. It will be deleted and re-created.

| Command                      | Description                                    |
| ---------------------------- | ---------------------------------------------- |
| `terraform taint vm1.name`   | Taint a specified resource instance.           |
| `terraform untaint vm1.name` | Untaint the already tainted resource instance. |

### Refresh the State File

```shell
terraform refresh
```

 Modify the state file with updated metadata containing information on the resources being managed in Terraform. Will not modify your infrastructure.

### Manipulate Statefile

`terraform state` Used with following subcommands

| Command                                                                               | Description                                                                                                                                                             |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `terraform state list`                                                                | Lists out all the resources that are tracked in the current state file.                                                                                                 |
| `terraform state mv`                                                                  | Move an item in the state, for example, this is useful when you need to tell Terraform that an item has been renamed, e.g. `terraform state mv vm1.oldname vm1.newname` |
| `terraform state pull > state.tfstate`                                                |  Get the current state and outputs it to a local file.                                                                                                                  |
| `terraform state push`                                                                |  Update remote state from the local state file.                                                                                                                         |
| ``terraform state replace-provider hashicorp/azurerm customproviderregistry/azurerm`` | Replace a provider, useful when switching to using a custom provider registry.                                                                                          |
| `terraform state rm`                                                                  | Remove the specified instance from the state file. Useful when a resource has been manually deleted outside of Terraform.                                               |
| `terraform state show <resourcename>`                                                 | Show the specified resource in the state file.                                                                                                                          |

### Import Existing Infrastructure into Your Terraform State

```shell
terraform import vm1.name -i id123
```
 — Import a VM with id123 into the configuration defined in the configuration files under vm1.name.

### Manage Terraform Workspaces
`terraform workspace` — One of the following subcommands must be used with the workspace command. Workspaces can be useful when an engineer wants to test a slightly different version of the code. It is not recommended to use Workspaces to isolate or separate the same infrastructure between different development stages, e.g. Dev / UAT / Production, or different internal teams.

| Command                                       | Description                                   |
| --------------------------------------------- | --------------------------------------------- |
| `terraform workspace show`                    | Show the name of the current workspace.       |
| `terraform workspace list`                    | List your workspaces.                         |
| `terraform workspace select <workspace name>` | Select a specified workspace.                 |
| `terraform workspace new <workspace name>`    | Create a new workspace with a specified name. |
| `terraform workspace delete <workspace name>` | Delete a specified workspace                  |

### View your outputs

| Command                                        | Description                                                                                                     |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `terraform output`                             | List all outputs currently held in your state file                                                              |
| `terraform output -state=<path to state file>` |  List the outputs held in the specified state file. **-state** option is ignored when the remote state is used. |
| `terraform output -json`                       |  List the outputs held in your state file in JSON format to make them machine-readable.                         |
| `terraform output vm1_public_ip`               | List a specific output                                                                                          |

### Release a Lock in your workspace
```shell
terraform force-unlock <lock_id>
```

Remove the lock with the specified lock ID from your workspace. Useful when a lock has become ‘stuck’, usually after an incomplete Terraform run.

### Log In and Out to a Remote Host (Terraform Cloud)

| Command                       | Description                                                                                                          |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `terraform login`             |  Grab an API token for Terraform cloud (app.terraform.io) using your browser.                                        |
| `terraform login <hostname>`  |  Log in to a specified host.                                                                                         |
| `terraform logout`            |  Remove the credentials that are stored locally after logging in, by default for Terraform Cloud (app.terraform.io). |
| ``terraform logout <hostname> | Remove the credentials that are stored locally after logging in for the specified hostname.                          |

### Produce a Dependency Diagram

| Command                        | Description                                                                                                                                                          |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `terraform graph`              | Produce a graph in DOT language showing the dependencies between objects in the state file. This can then be rendered by a program called Graphwiz (amongst others). |
| `terraform graph -plan=tfplan` | Produce a dependency graph using a specified plan file (generated using `terraform plan -out=tfplan`).                                                               |
| `terraform graph -type=plan`   |  Specify the type of graph to output, either `plan, plan-refresh-only, plan-destroy,` or `apply`.                                                                    |
| `terraform graph -draw-cycles` | You can see if there are any dependency cycles between the resources.                                                                                                |

### Test your expressions
`terraform console`

With the `terraform console` command, you have the ability to test different pieces of code. All you have to do is write `terraform console`, and then you can write HCL code.

```shell
terraform console

# The below command will merge list elements into a string, separating them with commas.
> join(",",["foo","bar"])
"foo,bar"

# The below command will do math operations
> 1 + 5
6

# You can use resource parameters to get details about them. With the below command, we will get the public ip of an ec2 instance called my_ec2
> aws_instance.my_ec2.public_ip
3.153.2.10
```

### Switch Working Directory
```shell
terraform -chdir=”../dev” apply
```

You also have the ability to run Terraform from another directory if the need arises. This is particularly useful when you are using different automations and you don’t want to change directory. 

### Shell Tab-completion
Terraform also comes with an optional Shell Tab-completion. It can be useful if you are just starting out with Terraform. However, Terraform CLI is pretty lightweight, and you won’t usually reach very long commands.

To install the Shell Tab-completion you will need to first run:

```shell
terraform -install-autocomplete
```

After that you will need to resource your profile. This is done by either closing and opening the terminal, or by running source _path_to_your_profile_.

