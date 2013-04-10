# README

[![Build Status](https://travis-ci.org/mlandauer/cuttlefish.png?branch=master)](https://travis-ci.org/mlandauer/cuttlefish)

Dependencies: Ruby 1.9.3, bundler

##To install:
```
bundle install
```

##To run:
```
bundle exec foreman start
```

##To install on your server:
Edit `config/deploy.rb`

Run:
```
cap deploy:setup
cap deploy:cold (the first time)
```

And on the server
```
cd /srv/www/cuttlefish.openaustraliafoundation.org.au/current
sudo foreman export upstart /etc/init -u deploy -a cuttlefish -f Procfile.production -l /srv/www/cuttlefish.openaustraliafoundation.org.au/shared/log --root /srv/www/cuttlefish.openaustraliafoundation.org.au/current
visudo
```

And add the following line:
```
deploy  ALL = NOPASSWD: /usr/sbin/service
```
This allows the deploy user to sudo just to manage the upstart processes

## New relic:
If you use new relic just put your configuration file in shared/newrelic.yml on the server
To record your deploys you will also need to add config/newrelic.yml on your local box. How annoying!
