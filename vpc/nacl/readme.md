# Get vpc id
aws ec2 describe-vpcs \
--filters "Name=tag:Name,Values=nacl-example-vpc" \
--query "Vpcs[].VpcId" \
--output text

# Create NACL
aws ec2 create-network-acl --vpc-id vpc-039af4b88b67b7363

# Add rule
 aws ec2 create-network-acl-entry \
 --network-acl-id acl-0efad260173da0b46 \
 --ingress \
 --rule-number 90 \
 --protocol -1 \
 --port-range From=0,To=65535 \
 --cidr-block 217.217.216.197/32 \
 --rule-action deny