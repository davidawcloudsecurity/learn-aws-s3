# learn-aws-s3

## How to upload multiple files to s3 bucket
```bash
for file in whatever*.txt; do { aws s3 cp $file s3://somewhere/in/my/bucket/; } done
```
