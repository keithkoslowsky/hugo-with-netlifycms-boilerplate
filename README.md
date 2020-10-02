- [ ] Signup for Github and Netlify (skip if have done already)

- [ ] Enable two step authentication for both Github and Netlify (skip if have done already)

- [ ] Download code for the website generator (cms version of the site), unzip it, and cleanup the zip file
 ```
 wget -O hugo-with-netlifycms-boilerplate-netlifycms.zip https://github.com/keithkoslowsky/hugo-with-netlifycms-boilerplate/archive/netlifycms.zip; unzip hugo-with-netlifycms-boilerplate-netlifycms.zip; rm hugo-with-netlifycms-boilerplate-netlifycms.zip
```

- [ ] Name your project in variables so you can copy and paste commands in the future
```
NEW_PROJECT_NAME=test-hugo
GITHUB_URL=git@github.com:XXXXX/${NEW_PROJECT_NAME}.git
```
**Change GITHUB_URL to your own string**

- [ ] In your [NEW_PROJECT_NAME] directory, make a new `netlifycms` empty branch
```
(cd $NEW_PROJECT_NAME; git checkout --orphan netlifycms; git rm -rf .)
```

- [ ] Copy files you just downloaded into your new project directory
```
cp -r hugo-with-netlifycms-boilerplate-netlifycms/* $NEW_PROJECT_NAME
```

- [ ] If you haven't created a Github repo for your project, do it now and make it private. If you have already done this, following the steps in the README.md from the `master` branch then skip this as the Github repo will host both the static site on the `master` branch and the cms on the `netlifycms` branch 

- [ ] Start working in the [NEW_PROJECT_NAME]
```
cd $NEW_PROJECT_NAME
```

- [ ] In the [NEW_PROJECT_NAME] directory, commit those files and push it up the Github repo you just made. 

- [ ] If already initiated git in the [NEW_PROJECT_NAME] directory then skip this step (already did this following the steps in `master` README.md)
```
git init
git remote add origin $GITHUB_URL
```

- [ ] Change the github folder to .github. By doing this, it will enable Github Actions to run when you push up the branch.
```
mv github .github; git add .github/
```

The Github Action pulls down the latest from the branch, downlods any dependencies, caches them for quicker use later, and pushes up the public directory to Netlify.

- [ ] Edit public/admin/config.yml and change `site_url` to your website that will display the static generated content (your read-only website, that you setup from the `master` branch). You can [change other settings](https://www.netlifycms.org/docs/configuration-options/) too.

- [ ] If you followed the steps in the README.md in the master branch, you have already created a Netlify site to host your static site. You will need to create a new Netlify site now to host your CMS

- [ ] Connect Github. Use the `netlifycms` branch. Leave all the build fields blank

- [ ] Go to Site settings->Build and deploy->Edit Settings and under Builds...Stop builds.

- [ ] In Github add a new secret...Settings->Secrets.
```
NETLIFY_SITE_ID_CMS - found in Netlify General tab...API ID

*Note: NETLIFY_AUTH_TOKEN - this will already exist if you followed the steps in the README.md on the `master` branch and got the static site up. If you did not do that, you will need to add NETLIFY_AUTH_TOKEN as well. Look at the `master` README.md on how to find that 
```

- [ ] You should disable Form detection in Netlify...Build & Deploy->Form detection

Push up netlifycms repo to Github
```
git add *; git commit -am 'initial commit'; git push origin netlifycms
```

Now change enable Identity in Netlify
- [ ] Identity->Enable Identity
- [ ] Git Gateway->Enable Git Gateway. Authorize.
- [ ] Settings->Identity->External providers. Add a provider, like Google. Use default configuration.
- [ ] Settings->Identity->Registration. Change to Invite Only.
- [ ] Click Identity tab (top of the page) and then Invite Users. Add email address linked to provider you just added. You are allowed 5 free users to invite

- [ ] Visit CMS URL. /admin/

- [ ] If you can add a gate around this domain via Netlify Access or basic authentication you should. Authentication is in the app but an extra layer of security will keep bots out and worry a little less about zero days

