CI/CD Pipeline that builds and deploys code to a dev, QA testing environment and then once a manual review is approved the changes are pushed to production. Triggers are setup to ensure the code can successfully build whenever a pull request is created, updated, reopend or code is pushed to a branch. Branch protection rules are set to ensure code pases staus check before being merged to main/master branch. 

