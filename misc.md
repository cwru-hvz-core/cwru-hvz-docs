=CWRU HvZ Documentation
This file is a dump of random notes I've taken over the past few months on how to develop for cwru-hvz-source. This project will have more structure eventually.

==Developing Locally
To get this running on your machine, pull down the source code and then run:

`bundle install`
* Note for macOS users: see issue 54 on github

Next, set up the development (and test?) databases using [this tutorial](https://www.digitalocean.com/community/tutorials/how-to-setup-ruby-on-rails-with-postgres) and the options in config/database.yml (e.g. hvz_dev)
^ if you installed postgres with a GUI like I did, you may not need to use su to impersonate the postgres user; just open the postgres terminal from the postgres app

`rake db:schema:load`

All Rake DB tasks: http://jacopretorius.net/2014/02/all-rails-db-rake-tasks-and-what-they-do.html

== Twilio Integration
To set up SMS integration with Twilio, set the following environment variables:
`TWILIO_ACCOUNT_SID, TWILIO_AUTH_TOKEN, TWILIO_PHONE_NUMBER`

Web server vs. app server:
http://www.justinweiss.com/articles/a-web-server-vs-an-app-server/

==Notes found on server
How do I do things?

The crontab contains code to start up the HvZ web and HvZ worker on reboot

Typically during the game, to allow for easy rebooting, I open up a tmux
and start up the web and worker in there (Kill them first by finding them with ps
and grep).

Do quick hacky shit by opening up a rails console
`RAILS_ENV=production bundle exec rails console`

When you update some code, just ctrl-c out of the foreman process and fire it
back up again.

RAILS_ENV=production /home/hvz/.rbenv/shims/foreman start web -d /home/hvz/cwru-hvz-source/
RAILS_ENV=production /home/hvz/.rbenv/shims/foreman start worker -d /home/hvz/cwru-hvz-source/