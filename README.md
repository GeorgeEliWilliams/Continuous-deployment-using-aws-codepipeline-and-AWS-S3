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
2. block all public access since this website will be open to the general public in this particular case
3. leave all other defaults and create bucket
4. after creating the bucket, go to properties(the bucket is not enabled by default to host a static website hence we need to enable it)
5. scroll down to static website hosting
6. click on edit and then click on enable and also fill in the index document as index.html
7. click on save changes
8. go to permissions to add a bucket policy to allow public read access
9. scroll down to bucket policy and click on edit
10. paste the bucket policy from the bucket poicy.py file and click save


#### Step 2: Create AWS CodePipeline
1. navigate to codepipeline
2. click on create pipeline
3. choose v1 as the pipeline type and hit next


#### Step 3: Connect GitHub to CodePipeline
1. on the source provider page, select github version 2
2. click on connect to github
3. give a connection name( in my case "meme-github-pipeline") and click on connect to github
4. authorize the github connection
5. click on install a new app
6. it will take you to your github profile where you will scroll to grant permissions to specific access to repositories and click on install
7. ready to connect
8. trigger the pipeline when there is a push to the repository and click on next
9. we will skip the build phase
10. for the deploy provider, select s3
11. fill in the details for your s3 bucket
12. also, select "extract file before deploy" and click on next
13. create the pipeline


#### Step 4: Monitor CodePipeline
Monitor the progress of the source and deploy stages of CodePipeline.


#### Step 5: Test the Static Website
1. navigate to the properties tab on s3
2. scroll down to static website hosting section and click on the website endpoint
3. view the game page
4. Make a minor change to the index.html file in the repository and commit it to test the pipeline trigger.
5. we can see that the trigger worked perfectly and the deployment to s3 was successful

## AND WE ARE DONE....