signup for Github and Netlify
Enable two step authentication for both Github and Netlify

Create a repository in Github and make it private.
Copy the files from hugo-with-netlifycms-boilerplate
mv github .github
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin [GITHUB_PROJECT_URL]
git push -u origin master

Create a new site in Netlify
Connect Github
Leave all the build fields blank
After it is Published, go into Site settings->Build and deploy->Edit Settings and under Builds...Stop builds.

In Github add two secrets...Settings->Secrets.
NETLIFY_SITE_ID - found in Netlify General tab...API ID
NETLIFY_AUTH_TOKEN - found in Netlify https://app.netlify.com/user/applications#personal-access-tokens Generate a new token for this site

Additional steps you should do in Netlify: Disable forms (unless you use them)

git commit --allow-empty
git push
Verify in Github Actions that the build was successful
Open Netlify URL to view live website