Create a new site in Netlify
Connect Github
Leave all the build fields blank
After it is Published, go into Site settings->Build and deploy->Edit Settings and under Builds...Stop builds.

In Github add a new secret...Settings->Secrets.
NETLIFY_SITE_ID_CMS - found in Netlify General tab...API ID

*Note: NETLIFY_AUTH_TOKEN - this will already exist

Additional steps you should do in Netlify: Disable forms (unless you use them)

Edit public/admin/config.yml and change site_url to your website that will display the static generated content

The boilerplate has a github directory. You should `mv github .github` in your project so the Github Action will run automatically

git push origin cms

Identity->Enable Identity
Settings and usage->External providers. Add a provider, like Google. Use default configuration.
Git Gateway->Enable Git Gateway. Authorize.
Click Identity and then Invite Users. Add email address linked to provider you just added. You are allowed 5 free users to invite
.

Visit CMS URL. /admin/
