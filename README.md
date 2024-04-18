# Meme Website Deployment with AWS CodePipeline

This repository contains the code and configuration files for deploying a static meme website using AWS CodePipeline.

## Getting Started

### Prerequisites

Before getting started, ensure you have the following:

- An AWS account
- GitHub account
- Basic understanding of AWS services like S3 and CodePipeline

### Installation

Follow these steps to deploy the meme website:

#### Step 1: Create and Configure S3 Bucket
1. navigate to s3 and create a bucket

![create bucket](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/19ecc6f9-1637-4d1d-890b-8a69072ecb9b)

2. block all public access since this website will be open to the general public in this particular case

![block all public access](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/b28435eb-7292-40c8-9960-40ad0315ac1c)

3. leave all other defaults and create bucket
4. after creating the bucket, go to properties(the bucket is not enabled by default to host a static website hence we need to enable it)
5. scroll down to static website hosting

![enable static website hosting](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/a9d12ba0-9b8f-4763-8b84-4325ff0d6677)

6. click on edit and then click on enable and also fill in the index document as index.html

![index document](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/1b8d8a77-4fb1-4b37-8f1b-f0fb2f6b70c7)

7. click on save changes
8. go to permissions to add a bucket policy to allow public read access
9. scroll down to bucket policy and click on edit

![scroll down to bucket policy and click on edit](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/fdb65bfc-a141-4c89-8b0b-4e2e91584386)

10. paste the bucket policy from the bucket poicy.py file and click save


#### Step 2: Create AWS CodePipeline
1. navigate to codepipeline
2. click on create pipeline

![create pipeline](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/cece24c3-cca5-4978-927e-b4d5a85f70c8)

3. choose v1 as the pipeline type and hit next

![v1](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/e8cbcbf4-76a2-4e1f-8601-7780e01dc41f)


#### Step 3: Connect GitHub to CodePipeline
1. on the source provider page, select github version 2
2. click on connect to github

![connect to github](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/9b99bb99-157b-4c6e-8f3d-af5a3faeee2d)

3. give a connection name( in my case "meme-github-pipeline") and click on connect to github

![connection name](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/1c52151d-49cd-40bb-bd67-6c48a5b17520)

4. authorize the github connection
5. click on install a new app

![install new app](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/fcdc777b-952b-4001-a83a-a8aadc535557)

6. it will take you to your github profile where you will scroll to grant permissions to specific access to repositories and click on install

![permissions for repositories](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/1530d772-bfb1-49d3-9854-d274993d22b7)

7. ready to connect

![ready to connect](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/0385c738-059d-4fed-a7d7-ac107316663c)

8. trigger the pipeline when there is a push to the repository and click on next

![trigger](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/7a5894da-205e-49bc-96ec-d277addceed1)

9. we will skip the build phase

![skip build phase](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/a80d0811-46bb-4eb8-8822-c785e59f28af)

10. for the deploy provider, select s3
11. fill in the details for your s3 bucket

![deploy stage](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/272dffd4-8fe8-4cca-852e-36fc913777c3)

12. also, select "extract file before deploy" and click on next
13. create the pipeline

![create final pipeline](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/022c4579-8f93-47fc-b7cf-9b8045c52a31)


#### Step 4: Monitor CodePipeline
Monitor the progress of the source and deploy stages of CodePipeline.

![pipeline progress](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/228efc12-5d0f-427a-ab59-f8507f129cef)


#### Step 5: Test the Static Website
1. navigate to the properties tab on s3
2. scroll down to static website hosting section and click on the website endpoint

![static website hosting endoint](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/4142b58a-fa8a-40ee-aade-6dfabbbd92f4)

3. view the game page

![game welcome page](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/c2e8e242-1616-4ebb-be2e-258c51c63941)

![game](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/55a06ab2-ac12-4ba7-b743-0d0ecb85f966)

4. Make a minor change to the index.html file in the repository and commit it to test the pipeline trigger.

![meme matching updated](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/188c0534-de05-4a13-9c79-081711034052)

5. we can see that the trigger worked perfectly and the deployment to s3 was successful

![meme match updtd](https://github.com/GeorgeEliWilliams/Continuous-deployment-using-aws-codepipeline-and-AWS-S3/assets/103576454/73441117-1a0e-4ea4-bfc9-168a8f8d7628)

## AND WE ARE DONE....