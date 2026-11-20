## Create a new bucket
aws s3 mb s3://cors-fun-mg-1241
## Create a block public access
aws s3api put-public-access-block \
--bucket cors-fun-mg-1241 --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"
## Apply Bucket Policy
aws s3api put-bucket-policy --bucket cors-fun-mg-1241 --policy file://cors-bucket-policy.json
## Turn on static website hosting
aws s3api put-bucket-website --bucket cors-fun-mg-1241 --website-configuration file://website.json
## Uploud index.html and upload a cors resource
aws s3 cp index.html s3://cors-fun-mg-1241
## View the website see if index is there
http://cors-fun-mg-1241.s3-website.eu-south-2.amazonaws.com

## Apply CORS policy
aws s3api put-bucket-cors --bucket cors-fun-mg-1241 --cors-configuration file://cors.json