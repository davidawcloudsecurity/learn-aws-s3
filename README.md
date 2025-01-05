# learn-aws-s3

### Create s3 bucket policy to allow iam:user access bucket
```bash
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::0123456789012:user/exampleuser"
            },
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:ListBucket",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::demo-bucket-1",
                "arn:aws:s3:::demo-bucket-1/*"
            ]
        }
    ]
}
```
### Create s3 bucket policy to get, put and not list iam:user access subfolder only
```bash
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::0123456789012:user/exampleuser"
            },
            "Action": [
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": "arn:aws:s3:::demo-bucket-2/dataset/*"
        }
    ]
}
```
or
```bash
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Principal": {
				"AWS": "arn:aws:iam::0123456789012:user/exampleuser"
			},
			"Action": "s3:ListBucket",
			"Resource": [
				"arn:aws:s3:::demo-bucket-2/dataset/*",
				"arn:aws:s3:::demo-bucket-2"
			],
			"Condition": {
				"StringLike": {
					"s3:prefix": "dataset/*"
				}
			}
		},
		{
			"Effect": "Deny",
			"Principal": {
				"AWS": "arn:aws:iam::0123456789012:user/exampleuser"
			},
			"Action": "s3:*",
			"Resource": [
				"arn:aws:s3:::demo-bucket-2",
				"arn:aws:s3:::demo-bucket-2/*"
			],
			"Condition": {
				"StringNotLike": {
					"s3:prefix": "dataset/*"
				}
			}
		}
	]
}
```
### Create s3 bucket policy to allow iam:user access subfolder within a folder or a role to access bucket
https://demo-bucket-3.s3.us-east-1.amazonaws.com/123/dataset/ctf03.flag
```bash
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::0123456789012:user/exampleuser"
            },
            "Action": "s3:ListBucket",
            "Resource": [
                "arn:aws:s3:::demo-bucket-3/*/dataset/*",
                "arn:aws:s3:::demo-bucket-3"
            ],
            "Condition": {
                "StringLike": {
                    "s3:prefix": "*/dataset/*"
                }
            }
        },
        {
            "Effect": "Deny",
            "Principal": {
                "AWS": "arn:aws:iam::0123456789012:user/exampleuser"
            },
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::demo-bucket-3",
                "arn:aws:s3:::demo-bucket-3/*"
            ],
            "Condition": {
                "StringNotLike": {
                    "s3:prefix": "*/dataset/*"
                }
            }
        },
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::0123456789012:role/s3role"
            },
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:ListBucket",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::demo-bucket-3/*",
                "arn:aws:s3:::demo-bucket-3"
            ]
        }
    ]
}
```

### How to 
- [ ] https://catalog.workshops.aws/aws101/en-US/1-getting-started/01-architecture
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
