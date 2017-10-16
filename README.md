# my-portfolio
Professional portfolio a cloud guru


Technologies used

git and github
ssh
html
css
route53
s3
iam
CodeBuild - get code from source, github, use container Ubuntu, s3 artifacts type, needs a service role.  YAML file, buildspec.yaml, place in root dir of project, output is files of portfolio, image/*, *.html. Put it in the code area of git and push to git hub.

Python, boto3, AWS CLI - CodeBuild puts a zip file in a different S3 bucket than the portfolio bucket.  Manually moves files into using iPython boto3, and AWS CLI unzip files.  Builds a script that will automatically do the work of unzip, upload and change perms. Call the .py lambda,

Lambda - triggered by build, runtime Python 2.7, paste script into Lambda on the Consolde, create role, set memory and time function can run

SNS - updates Lambda.py to provide status, use SNS to send messagea after building SNS subscription and Topic on SNS console, like email, sms.

CodePipeline - on Console, create PipeLine, Source=github, AWS codebuild from above, Create Role, Add Lambda as Custom Action after build, Invoke
Action, Provider = AWS Lambda,  Input is the Codebuild, lambda is the deploy.     CodePipeline creates its own Bucket S3, update lambda.py to deal 
codepipeline, and more permissions thru iam roles.

