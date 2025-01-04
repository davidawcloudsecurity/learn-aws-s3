# learn-aws-s3

### How to 
- [ ] https://catalog.workshops.aws/s3demystify/en-US
- [ ] https://d1.awsstatic.com/events/Summits/awsreinforce2023/DAP372_Demystifying-Amazon-S3-authentication-authorization-and-encryption.pdf
- [ ] https://aws.amazon.com/appstream2/getting-started/isv-workshops/saas/module-1/

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
