# SLUGRAM BACKEND
[![Build Status](https://travis-ci.org/slugbyte/slugram-backend.svg?branch=stageing)](https://travis-ci.org/slugbyte/slugram-backend)
[![Coverage Status](https://coveralls.io/repos/github/slugbyte/slugram-backend/badge.svg?branch=stageing)](https://coveralls.io/github/slugbyte/slugram-backend?branch=stageing)

Source: [https://github.com/slugbyte/slugram-backend](https://github.com/slugbyte/slugram-backend)

This repo is being used for deployment practice.

## Deployment Steps
### Back End
#### GitHub
Note: these instructions are for a Mac and may be different for other operating systems.

1. Create a new repo on GitHub sg-be with nothing added
1. Create a new folder locally called sg-be
1. Copy slugram-backend files to sg-be
1. Push an existing repository from the command line:
	1. `git remote add origin https://github.com/mmpadget/sg-be.git`
	1. `git push -u origin master`
2. Open both sg-be and slugram-backend in Atom
1. Copy over any hidden files
1. Add `node_modules/*` to gitignore file
1. `npm i` (to install node packages locally)
1. In command line: `mongo`
1. In new command line tab: `npm run start-debug`
1. Test API with Postman: `http://localhost:3000/api/`
1. (Optional) in browser console: `localStorage.clear()`
1. (Optional) change .env file (for reference only)
	1. Delete `PORT=3000`
	1. Update AWS bucket, key id, and access key
1. `git add`, commit, push to master

#### Heroku

1. Add a new app on Heroku (sg-be)
1. Install mLab MongoDB
	1. Go to: Settings
	1. Click: Find New Buildpacks at Heroku Elements
	1. Click: Add-ons
	1. Click: mLab MongoDB
	1. Click: Login to Install, Install mLab MongoDB
	1. Select application: sg-be
	1. Choose: Sandbox - Free
1. (Optional) update local .env file from Heroku (for reference only)
	1. Visit: Settings
	1. Click: Reveal Config Vars
	1. Note: `MONGODB_URI` and mongodb://
	1. Copy: mongodb:// and paste into local sg-be .env file
1. Update Heroku Config Vars
	1. Visit: Settings
	1. Click: Reveal Config Vars
	1. Click: Add
	1. Copy values from local .env file
		1. `APP_SECRET`
		1. `AWS_ACCESS_KEY_ID`
		1. `AWS_BUCKET`
		1. `AWS_SECRET_ACCESS_KEY`
		1. `NODE_ENV` (should be testing)
	1. **Do not change** `NODE_ENV=‘testing’` to `NODE_ENV=‘production’`
1. Create Heroku Git Repo
	1. Visit: Deploy (for customized commands)
	1. In command line:
		1. `git remote -v`
			1. `origin	https://github.com/mmpadget/sg-be.git (fetch)`
			1. `origin	https://github.com/mmpadget/sg-be.git (push)`
		1. `heroku git:remote -a sg-be`
		1. `git remote -v`
			1. `heroku	https://git.heroku.com/sg-be.git (fetch)`
			1. `heroku	https://git.heroku.com/sg-be.git (push)`
			1. `origin	https://github.com/mmpadget/sg-be.git (fetch)`
			1. `origin	https://github.com/mmpadget/sg-be.git (push)`
1. Deploy to Heroku
1. `git push heroku master`

#### Verify and Troubleshoot
1. In Heroku Click: Activity (to verify)
	1. Click: View build log
	1. Click: Settings (to copy Heroku domain for next step)
1. Test API with Postman: `https://sg-be.herokuapp.com/api/`
1. Click: Resources
	1. Click: mLab MongoDB :: Mongodb
