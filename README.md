- [ ] Signup for Github and Netlify

- [ ] Enable two step authentication for both Github and Netlify

- [ ] Download code for the website generator (read-only version of the site), unzip it, and cleanup the zip file
```
wget -O hugo-with-netlifycms-boilerplate-master.zip https://github.com/keithkoslowsky/hugo-with-netlifycms-boilerplate/archive/master.zip; unzip hugo-with-netlifycms-boilerplate-master.zip; rm hugo-with-netlifycms-boilerplate-master.zip
```
- [ ] Copy files you just downloaded into your new project directory
```
cp -r hugo-with-netlifycms-boilerplate-master [NEW_PROJECT_NAME]
```

- [ ] Create a repository in Github and make it private. In the [NEW_PROJECT_NAME] directory, commit those files and push it up the Github repo you just made. Instructions on how to do that will be provided when you create your repo in Github.

- [ ] Change the github folder to .github. By doing this, it will enable Github Actions to run when you push up the branch.
```
mv github .github
```

The Github Action pulls down the latest from the branch, downlod some dependencies, cache them for quicker use later, run the Hugo generator in production mode, and push up the dist directory from the build to Netlify.


- [ ] Create a new site in Netlify

- [ ] In the Netlify site, link the Github repo. Leave all the build fields blank

- [ ] After it is Published, go into Site settings->Build and deploy->Edit Settings and under Builds...Stop builds

- [ ] In Github add two secrets...Settings->Secrets.
```
NETLIFY_SITE_ID - found in Netlify General tab...API ID
NETLIFY_AUTH_TOKEN - found in Netlify https://app.netlify.com/user/applications#personal-access-tokens Generate a new token for this site
```

- [ ] Additional step you should do in Netlify: Disable forms (unless you use them)

```
git commit --allow-empty
git push
```

- [ ] Verify in Github Actions that the build was successful
- [ ] Open Netlify URL to view live website
