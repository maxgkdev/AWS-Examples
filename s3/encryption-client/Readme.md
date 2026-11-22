## Create a new bucket
aws s3 mb s3://encrypt-client-fun-mg-1241

## Run our SDK RUby Scrypt, encrypt

bundle exec ruby encrypt.rb

## Cleanup

aws s3 rm s3://encrypt-client-fun-mg-1241/hello.txt
aws s3 rb s3://encrypt-client-fun-mg-1241