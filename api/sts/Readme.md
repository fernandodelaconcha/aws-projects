## Create a user with no permissions

aws iam create-user --user-name sts-machine-user

aws iam create-access-key --user-name sts-machine-user --output table

aws configure

## See credentials

open ~/.aws/credentials

## Test who you are

aws sts get-caller-identity --profile sts

## Make sure you dont have access to s3

aws s3 ls --profile sts

## Create a role

chmod u+x bin/deploy

## Use new user credentials and assume role

aws iam put-user-policy \
--user-name sts-machine-user \
--policy-name StsAssumePolicy \
--policy-document file://policy.json

aws sts assume-role \
--role-arn arn:aws:iam::653827723644:role/my-sts-fun-stack-fernando-StsRole-c1OEUIOv0mLz \
--role-session-name s3-sts-fun \
--profile sts

aws sts get-caller-identity --profile assumed

aws s3 ls --profile assumed

## Delete policy

aws iam delete-user-policy --user-name sts-machine-user --policy-name StsAssumePolicy

## Delete access-keys

aws iam delete-access-key --access-key-id AKIAZQOZLKF6DN5LDAFQ --user-name sts-machine-user

## Delete user

aws iam delete-user --user-name sts-machine-user