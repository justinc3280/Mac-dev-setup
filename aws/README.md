# AWS Setup

## Create IAM Access Key
From the AWS console, configure an IAM user's access key credentials by following the steps [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-authentication-user.html#cli-authentication-user-get).

## Setup [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)
`brew install awscli`  

`aws configure`  
Enter the IAM credentials created in the previous step.

## Install [SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html)
`brew install aws/tap/aws-sam-cli`
