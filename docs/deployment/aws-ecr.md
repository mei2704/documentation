---
layout:         doc
title:          "AWS ECR - Documentation"
category:       "deployment"
logo:           aws-ecr
order:          6
excerpt:        "Deploy your containers to AWS ECR in a few clicks."
---

[AWS ECR](https://aws.amazon.com/ecr) is a fully-managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images.

## Specify your AWS credentials
To deploy to your AWS account, continuousphp needs access keys for IAM users. You can specify them in the 1st step of the project
setup or simply when adding a new pipeline to your existing project.

![AWS IAM credentials](/assets/doc/deployment/aws-ecr/iam-credentials.png)

## Configure the Packaging
After having configured the tests in the second step, you can now enable Docker in the Packaging configuration.

![AWS packing](/assets/doc/deployment/aws-ecr/packaging.png)

## Configure the Deployment
Once you have added the IAM credentials and you defined Docker as packaging method, you can configure the deployment in the 4th step of the project/pipeline setup.

![AWS deployment](/assets/doc/deployment/aws-ecr/destination.png)

## Use environment variables to define your tags
continuousphp provides you with a set of built-in environment variables that you can use to define your tags. Moreover you may want to truncate those variables then you can use the following syntax :

* ***CPHP_GIT_COMMIT*** : 225ff5830d804093869e5d8b6516aa7b
* ***${CPHP_GIT_COMMIT}*** : 225ff5830d804093869e5d8b6516aa7b
* ***${CPHP_GIT_COMMIT:0,7}*** : 225ff58
* ***${CPHP_GIT_COMMIT:7}*** :  30d804093869e5d8b6516aa7b
* ***${CPHP_GIT_COMMIT:-12}*** :  5d8b6516aa7b

!!! note "**IMPORTANT**"
    Make sure that the IAM credentials you provide only have the strict minimum of permissions. For instance
    the provided IAM credentials shouldn't be able to erase your ECR repository.

And that's it! You just configured your Dockerfile to be deployed with AWS ECR.
