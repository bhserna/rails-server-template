# Rails Server Template

## Overview

This is a template chef structure for deploying Rails applications. It's
primarily aimed at projects that want everything running on a single VPS
but don't want to use a SaaS platform such as Heroku.

## Usage

Clone the repo

```
git clone git@github.com:bhserna/rails-server-template.git
```

and run

```
bundle install
```

within `/data_bags/users/` user the deploy.json.example, to create a
real deploy.json file.

run

```
mkdir cookbooks
bundle exec berks install
bundle exec knife solo prepare root@yourserverip
```

This will generate a fil `nodes/yourserverip.json`. Copy the contents of
`nodes/rails_postgres_redis.json.example` and update the password of
the postgres user (you can use `openssl passwd -1
"plaintextpassword"` to generate the password)

run

```
bundle exec knife solo prepare root@yourserverip
```

## Common problems :cry:

There is a problem somtimes because the locales of the server are not
set. If that is the problem you can ssh to the server an set each
variable that is not set:

```
export LANGUAGE="en_US.UTF-8"
```

and then manually install postgress

```
apt-get install postresql-9.1
```
