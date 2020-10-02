- [ ] Signup for Github and Netlify

- [ ] Enable two step authentication for both Github and Netlify

- [ ] Download code for the website generator (read-only version of the site), unzip it, and cleanup the zip file
```
wget -O hugo-with-netlifycms-boilerplate-master.zip https://github.com/keithkoslowsky/hugo-with-netlifycms-boilerplate/archive/master.zip; unzip hugo-with-netlifycms-boilerplate-master.zip; rm hugo-with-netlifycms-boilerplate-master.zip
```

- [ ] Name your project in variables so you can copy and paste commands in the future
```
NEW_PROJECT_NAME=test-hugo
GITHUB_URL=git@github.com:XXXXX/${NEW_PROJECT_NAME}.git
```
**Change GITHUB_URL to your own string**

- [ ] Copy files you just downloaded into your new project directory
```
cp -r hugo-with-netlifycms-boilerplate-master $NEW_PROJECT_NAME
```

- [ ] Create a repository in Github and make it private. 

- [ ] Start working in the [NEW_PROJECT_NAME]
```
cd $NEW_PROJECT_NAME;
```

- [ ] In the [NEW_PROJECT_NAME] directory, commit those files and push it up the Github repo you just made. 
```
git init; git add * .gitignore .hugo_version .netlify-cli_version;  git remote add origin $GITHUB_URL
```

- [ ] Change the github folder to .github. By doing this, it will enable Github Actions to run when you push up the branch.
```
mv github .github; git add .github/
```

The Github Action pulls down the latest from the branch, downlods any dependencies, caches them for quicker use later, run the Hugo generator in production mode, and push up the dist directory from the build to Netlify.

- [ ] Create a new site in Netlify

- [ ] In the Netlify site, link your newly created Github repo. Use the `master` branch. Leave all the build fields blank

- [ ] Go into Site settings->Build and deploy->Edit Settings and under Builds...Stop builds

- [ ] You should disable Form detection in Netlify...Build & Deploy->Form detection

- [ ] In Github add two secrets...Settings->Secrets.
```
NETLIFY_SITE_ID - found in Netlify General tab...API ID
NETLIFY_AUTH_TOKEN - found in Netlify https://app.netlify.com/user/applications#personal-access-tokens Generate a new token for this site
```

Push up everything to Github
```
 git commit -am 'inital commit'; git push -u origin master
```

- [ ] Verify in Github Actions that the build was successful

- [ ] Open Netlify URL to view live website
