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
give a connection name( in my case "meme-github-pipeline") and click on connect to github
authorize the github connection
click on install a new app
it will take you to your github profile where you will scroll to grant permissions to specific access to repositories and click on install
click on connect on the main page
ready to connect
trigger the pipeline when there is a push to the repository and click on next
we will skip the build phase
for the deploy provider, select s3
fill in the details for your s3 bucket
also, select "extract file before deploy" and click on next
create the pipeine 
step 4. Monitoring the progress of the source and deploy stages of CodePipeline
step 5. Testing that the static website is working on S3
navigate to the properties tab on s3
scroll down to static website hosting section and click on the website endpoint
view the game page
to check if the pipeline trigger is working, we make a minor change to the index.html file and commit it