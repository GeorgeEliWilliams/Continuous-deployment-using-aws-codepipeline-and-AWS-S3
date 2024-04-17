steps
step 1.  Creat and configure an S3 bucket for static website hosting
- navigate to s3 and create a bucket
block all public access since this website will be open to the general public in this particular case
leave all other defaults and create bucket
after creating the bucket, go to properties(the bucket is not enabled by default to host a static website hence we need to enable it)
scroll down to static website hosting 
click on edit and then click on enable and also fill in the index document as index.html
click on save changes
go to permissions to add a bucket policy to allow public read access
scroll down to bucket policy and click on edit
paste the bucket policy from the bucket poicy.py file and click save
step 2. Creating a new pipeline in AWS CodePipeline
- navigate to codepipeline
click on create pipeline
choose v1 as the pipeline type and hit next
step 3. Connecting to GitHub from CodePipeline
- on the source provider page, select github version 2
click on connect to github
step 4. Monitoring the progress of the source and deploy stages of CodePipeline
step 5. Testing that the static website is working on S3