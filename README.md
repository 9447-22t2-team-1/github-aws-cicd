
# CI/CD Pipeline
CI/CD Pipeline that builds and deploys code to a dev, QA testing environment and then once a manual review is approved the changes are pushed to production. Triggers are setup to ensure the code can successfully build whenever a pull request is created, updated, reopend or code is pushed to a branch. Branch protection rules are set to ensure code passes staus check before being merged to main/master branch. 

# Setup

This repository contains 3 files that build the CI/CD pipeline:
pipeline.yaml   -> configures and creates the pipelies
buildspec.yaml  -> add commands to build the specfied application
deployspec.yaml -> add commands to deploy your application i.e ec2, lamda, s3 etc.


1. create a personal access token and save in aws secrets manager as (GITHUB_ACCESS_TOKEN)
2. update build spec i.e to build a Java application run maven commands build/clean/tests and
3. add branch protection rules -> require status check before merging
4. get aws credentials 
5. pip install awscli
6. aws configure create default profile
7. run the below command to deploy cloudformation stack from aws cli:
 aws cloudformation deploy --stack-name github-aws-cicd --template-file pipeline.yaml  --capabilities CAPABILITY_NAMED_IAM --parameter-overrides GithubRepository=github-aws-cicd

(capablilities IAM --paramter) overides to pass non-default paramters

8. create a PR to check which should trigger codebuild status check
9. merge code to master branch which automatically triggers codepipeline 
10. to view the pipeline on the aws console goto to aws code pipline


