# Redis buildpack

This buildpack gives you a per-dyno redis instance
for caching purposes (`127.0.0.1:6379`).


## Installation

Just add the buildpack:

`heroku buildpacks:add -a <app-name> -i 1 https://github.com/IDAGIO/heroku-buildpack-redis.git`

And set the max amount of memory that redis is allowed to use (this is **required**, there is no default):

`heroku config:set -a <app-name> LOCAL_REDIS_MAX_MEMORY=512M`


## Remember!

* The RAM that you allocate to redis will not be available to your app instance (mind the dyno size)
* Even a tiny cache often goes a [long way](https://en.wikipedia.org/wiki/Pareto_distribution)
* All data is erased every time the dyno restarts (which happens [automatically at least once per day](https://devcenter.heroku.com/articles/dynos#automatic-dyno-restarts))

