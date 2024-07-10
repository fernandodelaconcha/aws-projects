
## Create Bucket
aws s3 mb s3://bucket-policy-test-petazetas

## Change policy
aws s3api put-bucket-policy --bucket bucket-policy-test-petazetas --policy /s3/bucket-policy/policy.json