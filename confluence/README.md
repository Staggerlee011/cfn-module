# cfn-modules: confluence Install

Installs confluence container from dockerhub and hosts db on postgres-rds. 

## Prerequisites

1. [Install Node.js 10.x](https://nodejs.org/)
1. Create $Bucketname var `$BucketName = "fargate-confluence`
1. Create the bucket `aws s3 mb s3://$BucketName`

## Usage

```
npm i
aws cloudformation package --template-file confluence.yml --s3-bucket $BucketName --output-template-file packaged.yml
aws cloudformation deploy --template-file packaged.yml --stack-name fargate-confluence --capabilities CAPABILITY_IAM
aws cloudformation describe-stacks --stack-name fargate-confluence --query "Stacks[0].Outputs[?OutputKey=='Url'].OutputValue" --output text
```

Open the URL in your web browser.

Don't forget to delete the stack once you are done with the demo:

```
aws cloudformation delete-stack --stack-name fargate-confluence
```

## Modules

Find all modules here: https://www.npmjs.com/org/cfn-modules
