# Deploying on Heroku
https://hackmd.io/ev10gK4GSICmkk4yi12r_g?view

## The fast way: through the GUI
(Courtesy of Denis)
This is undoubtedly the easy way and it should be fine when everything runs smoothly. However, you are encouraged to consult the Heroku docs and learn how to deploy a project via your terminal, because that's where you'll need to turn to if there are glitches.
1. Log into your web Heroku account and go to the dashboard.
2. On the top right, click `Create new app`.
3. In the `App name` box, type a name for your app, then click `Create app`.
4. This will take you to a new page. Go to the `Deployment method` section and click the `Connect to GitHub` option. You may be asked to authorise Heroku.
5. In the `Connect to GitHub` section, you should see your GitHub alias under`Search for a repository to connect to`. If not, type it in, then click `Search`. This will return a list of all your GitHub repos.
6. Select from the list the repo you want to deploy, then click `Connect`.
7. In the `Manual deploy` section, click `Deploy branch`. Heroku will run a bunch of commands in the _Build master_ window. Once it's done, click `View` to see and try out your now live app. You can grab the URL for your app from the address bar.
8. If you need to tweak your app's configuration, go to your app's `Settings` and make your changes.

* Heroku allows you to deploy for free a maximum of five apps. If you need to delete an app from Heroku (this will not affect the code stored in your GitHub repo) to reclaim your free credit, click on your app's name, then go to `Settings` and find the `Delete app...` right at the bottom. Click the button, enter your app's name manually, confirm the deletion and you're done.


## The official way - through the terminal
1. Start with a look at the documentation:
https://devcenter.heroku.com/articles/getting-started-with-nodejs
There's lots of it, but, overall, it's well written. It's worth trying out their demo app to familiarise yourselves with the procedure. 
2. If you haven't tried out the demo app, follow the online guide to install Heroku on your machine. For your team projects, only one member of your team needs to  create a Heroku account, install Heroku CLI locally and log into Heroku (you will be asked to type in your terminal your Heroku account credentials).
3. Follow the online guide to configure your autocomplete app to use both your localhost port and whichever port Heroku specifies. 
The example at step '[Push local changes](https://devcenter.heroku.com/articles/getting-started-with-nodejs#push-local-changes)' in the official docs shows you how to do this in your `index.js` (or whatever you've named that file). Ignore the 'express' bit for now - you're not using Express for this project:
`const PORT = process.env.PORT || 5000`
4. Make sure that you add your 'start' script to your package.json.
5. Create the Procfile. The online docs ask you to 'define a Procfile', but you actually need to create it in your project's root folder. You can do so in your terminal:
`$ touch Procfile`
Read more about what this file does and what goes in it [here](https://devcenter.heroku.com/articles/deploying-nodejs#specifying-a-start-script).
6. If you've followed the official guide, you'll have already created the Heroku app. If you haven't already done so, now's the time:
`$ heroku create`
7. Deploy your app on Heroku: if you have unsaved changes in the code you want to deploy, make sure that you `git add .` and `git commit -m` (plus your message) before you push to Heroku. Once you're ready:
`$ git push heroku master`
8. Activate the live app on Heroku's server:
`$ heroku open`
9. Check that all's gone well and your app is up and running:
`heroku ps:scale web=1`
10. Check that you can still run it locally too. Enter
`$ heroku local web`
and open the port you're using on `localhost:` in your browser.

Handy links:
* The official Heroku documentation:
https://devcenter.heroku.com/articles/getting-started-with-nodejs
* [Node.js on Heroku: A More Complete Tutorial:Part 1](https://codeburst.io/node-js-on-heroku-a-more-complete-tutorial-part-1-9e80cb071498)
Parts 2 & 3 are also useful.

