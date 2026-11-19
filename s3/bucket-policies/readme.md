## Create a new bucket


aws s3 mb s3://bucketpolicy-fun-mg-1241


## Apply Policy

aws s3api put-bucket-policy --bucket bucketpolicy-fun-mg-1241 --policy file://policy.json

## In the other account acces the bucket

touch bootcamp.txt

aws s3 cp bootcamp.txt s3://bucketpolicy-fun-mg-1241

aws s3 ls s3://bucketpolicy-fun-mg-1241

## Cleanup

aws s3 rm s3://bucketpolicy-fun-mg-1241/bootcamp.txt

aws s3 rb s3://bucketpolicy-fun-mg-1241
