heroku-buildpack-clamav
========================

A [heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for setting up a clamd daemon.

## Usage

1. Add heroku buildpack apt: `heroku buildpacks:add --index 1 heroku-community/apt`
1. Add `Aptfile` in root directory with content `clamav clamav-daemon clamav-freshclam`
1. Add this buildpack in `app.json`:  `{ "url": "https://github.com/riskmethods/heroku-buildpack-clamav" }`
1. Change `Procfile` worker line to this: `worker: bin/start-clamd bundle exec sidekiq`
