# Upload to S3 with AWS CLI
Files can be uploaded to an S3 bucket through the command line interface using the AWS CLI. 

## Getting Started

### 1. Installation
To install the AWS CLI it is best to use a package manager such as Anaconda or Homebrew (MacOS).

**Anaconda**<br><br>
```conda install -c conda-forge awscli```

**Homebrew**<br><br>
```brew install awscli```

Alternatively, the package can be downloaded as a .zip and installed directly on your system. Refer to the [AWS documentation](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux-mac.html) for information on how to install the AWS CLI version 2 from a .zip file.

Finally, to confirm that it was installed properly run the command:<br><br>
```aws --version```

### 2. Configuration
The next step is to configure the AWS CLI client with your security credentials. To do this we require an Access Key ID and Secret Access Key. For information on what these are refer to the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) on security credentials.

Run the command:<br><br>
```aws s3 configure```

You will be prompted for the Access Key ID, Secret Access Key, region and output format. An example of a region would be `us-east-2`. Confirm that your are using the correct region for your project. Enter your security credentials, region and leave the output format as `json`. 

Once configuration is successful, the next step is to upload a file to the bucket.

## Uploading Files to S3 Bucket
Local files can be uploaded to S3 using the `aws s3 cp` command:<br><br>
```aws s3 cp <local path> <bucket URI>```

A bucket URI is simply the name of the bucket with the `s3://` prefix:<br><br>
```s3://<bucket name>```

 For example, if you're file is named "mytextfile.txt" and your bucket name is "my-cool-s3-bucket" you would run:<br><br>
```aws s3 cp mytextfile.txt s3://my-cool-s3-bucket```

To confirm that the file was successfully uploaded, list the files in the bucket by running:<br><br>
```aws s3 ls <bucket name>```

For example, if the bucket name is "my-cool-s3-bucket" you would run:<br><br>
```aws s3 ls s3://my-cool-s3-bucket```

## Troubleshooting
It is not uncommon to encounter an Access Denied message. This indicates that the user does not have IAM permissions to perform the desired access. Contact the AWS account administrator to add the desired actions (List, Read, Write) to the user's policy.

## Additional Information
[What Is the AWS Command Line Interface?](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)<br>
[AWS CLI Command Reference – S3](https://docs.aws.amazon.com/cli/latest/reference/s3/index.html#cli-aws-s3)

