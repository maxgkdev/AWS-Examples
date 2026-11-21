## Create a new bucket
aws s3 mb s3://encrypt-fun-mg-1241

## Create a file and put object with SS3-S3
echo "Hello World" > hello.txt
aws s3 cp hello.txt s3://encrypt-fun-mg-1241

## Put object with encyrption of kMS
aws s3api put-object --bucket encrypt-fun-mg-1241 \
--key hello.txt \
--body hello.txt \
--server-side-encryption "aws:kms" \
--ssekms-key-id "[The key you generate]"

## Put object with encyrption of SSE-C
export BASE64_ENCODED_KEY=$(openssl rand 32 | base64)
echo "$BASE64_ENCODED_KEY"

export MD5_VALUE=$(echo -n "$BASE64_ENCODED_KEY" | base64 --decode | openssl dgst -md5 -binary | base64)
echo "$MD5_VALUE"

aws s3api put-object --bucket encrypt-fun-mg-1241 \
--key hello.txt \
--body hello.txt \
--sse-customer-algorithm AES256 \
--sse-customer-key "$BASE64_ENCODED_KEY" \
--sse-customer-key-md5 "$MD5_VALUE"






## Cleanup

aws s3 rm s3://encrypt-fun-mg-1241/hello.txt
aws s3 rb s3://encrypt-fun-mg-1241

