## Create a bucket

aws s3 mb s3://metadata-fun-mg-1241

### Create a new file

echo "Hello Mars" > hello.txt

## Upload file with metada

aws s3api put-object --bucket metadata-fun-mg-1241 --key hello.txt --body hello.txt --metadata Planet=Mars

## Get metadata through head object

aws s3api head-object --bucket metadata-fun-mg-1241 --key hello.txt 

## Cleanup

aws s3 rm s3://metadata-fun-mg-1241/hello.txt

aws s3 rb s3://metadata-fun-mg-1241