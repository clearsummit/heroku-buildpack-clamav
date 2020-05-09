heroku-buildpack-clamav
========================

A [heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for setting up a clamd daemon.

## Usage

1. Add heroku buildpack apt: `heroku buildpacks:add --index 1 heroku-community/apt`
1. Add `Aptfile` in root directory with content `clamav clamav-daemon clamav-freshclam`
1. Add this buildpack in `app.json`:  `{ "url": "https://github.com/riskmethods/heroku-buildpack-clamav" }`
1. Change `Procfile` worker line to this: `worker: bin/start-clamd bundle exec sidekiq`


## Notes
The only change in this buildpack is to not install the virus definiations at slug compile time.  Instead the worker that needs them should add a `.profile` file to pull the virus definitions on boot.  This was done because the virus definitions are ~200MB-300MB, and the max slug size on Heroku is 500MB.
