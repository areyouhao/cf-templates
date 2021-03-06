# s3-for-static-website-hosting-with-cf
This template can be used to provision resources required to host a static website generated using hugo or jekyll. Template provisions an S3 bucket where the web site content can be stored and configures it for static website hosting as well as a cloudfront distribution configured with S3 Origin and creates a bucket policy on the S3 bucket to grant read only rights to content stored in S3 bucket to Cloud front Origin Access Identity (OAI). Additionally template also provisions a Route 53 hosted zone for the web site domain and creates a DNS A Record to map to cloudfront distribution and an IAM user with a policy that grants the user rights to add/update/delete items into S3 bucket where website content is stored, helpful for setting up CI process that generates site content and publish to S3 bucket 

## Parameters
Following parameters need to be passed when creating the stack

Parameter Name                      |   Purpose
------------------------------      |   -----------------------------------------------------------------------
BucketName                          |   Name to be used for S3 bucket where website content will be stored
Domain                              |   Custom domain name for your website
IndexDocument                       |   Index document to be used, Default index.html
ErrorDocument                       |   Error document to be used, Default error.html
PriceClass                          |   Cloudfront price class "PriceClass_All", "PriceClass_100", "PriceClass_200"
UserName                            |   Build User Name (For CI Builds, This user gets full rights to S3 bucket created as well as Cloudfront permissions required for invalidating distribution)
## Launching the stack
Running create-stack.sh script from terminal window will create the stack using the aws cli. Default parameters and stack name is picked up from the template.parameters.json. If you need to change the default values simply edit the template.parameters.json file.

```
./create-stack.sh
```


## Deleting the stack
You can delete the stack by running "delete-stack.sh" script from a terminal window as shown below.

```
./delete-stack.sh
```

