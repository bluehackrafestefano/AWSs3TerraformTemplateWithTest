# Terraform AWS S3

This folder contains a simple Terraform module that deploys 2 [S3
Buckets](https://aws.amazon.com/s3/) - one S3 Bucket with logging and versioning enabled, and another "targetBucket" one to serve as a
logging location for the first S3 Bucket. This module gives both Buckets a `Name` & `Environment` tag with the value 
specified in the `tag_bucket_name` and `tag_bucket_environment` variables, respectively. This module also contains a terraform variable 
that will create a basic bucket policy that will restrict the "origin" bucket to only accept SSL connections.
Also, bucket is encrypted with KMS.

Note that the S3 Buckets in this module will not contain any actual objects/files after creation; they will only contain a 
versioning and logging configuration, as well as tags.


## Running this module manually

1. Sign up for [AWS](https://aws.amazon.com/).
1. Configure your AWS credentials using one of the [supported methods for AWS CLI
   tools](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html), such as setting the
   `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables. If you're using the `~/.aws/config` file for profiles then export `AWS_SDK_LOAD_CONFIG` as "True".
1. Set the AWS region you want to use as the environment variable `AWS_DEFAULT_REGION`.
1. Install [Terraform](https://www.terraform.io/) and make sure it's on your `PATH`.
1. Run `terraform init`.
1. Run `terraform apply`.
1. When you're done, run `terraform destroy`.




## Running automated tests against this module

1. Sign up for [AWS](https://aws.amazon.com/).
1. Configure your AWS credentials using one of the [supported methods for AWS CLI
   tools](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html), such as setting the
   `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables. If you're using the `~/.aws/config` file for profiles then export `AWS_SDK_LOAD_CONFIG` as "True".
1. Install [Terraform](https://www.terraform.io/) and make sure it's on your `PATH`.
1. Install [Golang](https://golang.org/) and make sure this code is checked out into your `GOPATH`.
1. `cd test`
1. `dep ensure`
1. `go test -v -run TestTerraformAwsS3Example`