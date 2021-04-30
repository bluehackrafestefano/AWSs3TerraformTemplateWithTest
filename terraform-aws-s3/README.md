## This Terraform module deploys an S3 bucket with objects, and a log bucket to send the logs
- Main initial features are:
  - KMS key is used to encrypt bucket objects,
  - Logging is enabled, and a log bucket will be created within the main bucket,
  - Tags can be added as a variable,
  - Versioning is enabled,
  - Bucket will be private.

### How to use the module
- To use this module fallow the steps below:
  - Sign up for [AWS](https://aws.amazon.com/).
  - Configure your AWS credentials using one of the [supported methods for AWS CLI
   tools](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html), such as setting the
   `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables. If you're using the `~/.aws/config` file for profiles then export `AWS_SDK_LOAD_CONFIG` as "True".
  - Set the AWS region you want to use as the environment variable `AWS_DEFAULT_REGION`.
  - Install [Terraform](https://www.terraform.io/) and make sure it's on your `PATH`.
  - Clone the repo to the local working directory.
    ```bash
    git clone https://github.com/bluehackrafestefano/AWSs3TerraformTemplateWithTest.git
    ```
  - Navigate to the repository directory.
  - Initialize the Terraform project.
  ```bash
  terraform init
  ```
  - Make a plan and investigate the resources you are about to provision.
  ```bash
  terraform plan
  ```
  - Apply this configuration to create your S3 bucket and objects.
  ```bash
  terraform apply
  ```
  - Confirm by typing yes at the prompt.

### Variables
- Region, default is "us-east-1"
- Tags, defaults are "Terraform bucket" and "Dev".

### Outputs
- Bucket name and arn,
- Log bucket name and arn.

### How to test the module
- Install [Golang](https://golang.org/) and make sure this code is checked out into your `GOPATH`. (if you haven't already).
- Create a go working directory, where you want to work.
- Add this directories path to GOPATH env variable.
- Go to the working directory.
- Clone the repo as described above.
- Go to the test directory.
- To enable dependency tracking for your code by creating a go.mod file, run the go mod init command, giving it the name of the module your code will be in. The name is the module's module path. In most cases, this will be the repository location where your source code will be kept, such as github.com/mymodule. If you plan to publish your module for others to use, the module path must be a location from which Go tools can download your module.
```go
go mod init example.com/test
``` 
- Match the go.mod file with the dependencies required in the source files. Download all the dependencies that are required in your source files and update go. Basically we are calling code in an external package.
```go
go mod tidy
``` 
- Run the test in verbose mode. This will start our test.
```go
go test -v
``` 
- Source: https://golang.org/doc/tutorial/getting-started