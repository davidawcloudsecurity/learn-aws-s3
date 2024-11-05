# learn-aws-s3

### How to centralize s3 bucket
![image](https://github.com/user-attachments/assets/bc35b306-6569-42ed-becc-1023643a6cba)
### How to upload multiple files to s3 bucket
```bash
for file in whatever*.txt; do { aws s3 cp $file s3://somewhere/in/my/bucket/; } done
```
### YT Ideas
```bash
https://repost.aws/knowledge-center/s3-access-bucket-restricted-to-vpc
```
