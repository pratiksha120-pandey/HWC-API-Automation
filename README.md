# AAM-automation
this is about HWC application with Newman cli
STEP 1
Open Postman
Export your Collection → save as collection.json
Export your Environment → save as environment.json

STEP 2
Create a folder
Example: HWC-API-Automation
Copy both files (collection.json and environment.json) into this folder


STEP 3
Open Git Bash and go inside your folder
cd HWC-API-Automation

Create workflow folders:

mkdir .github
cd .github
mkdir workflows
cd workflows
touch newman-ci.yml
cd ../..

STEP 4
Check Node and NPM versions

node -v
npm -v


Create package.json:

npm init -y


STEP 5
Install Newman

Global install:

npm install -g newman newman-reporter-htmlextra


Local install (recommended):

npm install newman newman-reporter-htmlextra --save-dev


Verify:

newman -v


STEP 6
Run collection locally and generate report

newman run collection.json ^
-e environment.json ^
-r cli,htmlextra ^
--reporter-htmlextra-export report.html


Open report.html in browser to confirm.

STEP 7
Create a GitHub repository
Name: HWC-API-Automation

STEP 8
Push project to GitHub

git init
git add .
git status
git commit -m "Initial API automation setup"
git branch -M main
git remote add origin https://github.com/pratiksha120-pandey/HWC-API-Automation.git
git push -u origin main


STEP 9
Add GitHub Secrets

Go to:
Repository → Settings → Secrets and variables → Actions → New repository secret

Add:

EMAIL_USERNAME  = your Gmail ID
EMAIL_PASSWORD  = Gmail App Password
EMAIL_TO        = recipient email IDs (comma separated)


STEP 10
Open newman-ci.yml 
Paste your GitHub CI workflow code (Newman + Schedule + Email)

Save the file.

STEP 11
Run workflow manually

GitHub → Actions → Postman Newman CI
Click Run workflow

STEP 12
Automation Flow

Postman → Newman → GitHub Actions → HTML Report → Email


Your API automation pipeline is now complete.
