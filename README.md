# Heroku OAuth Example: Ruby

Example Ruby/Sinatra application that uses the Heroku OAuth web flow for authentication.

The [OAuth developer documentation](https://devcenter.heroku.com/articles/oauth?preview=1) has additional resources.

## Local Installation

```
heroku plugins:install heroku-cli-oauth
heroku clients:create -s "Localhost Example" http://localhost:5000/auth/heroku/callback
$ cat > .env <<EOF
HEROKU_OAUTH_ID=     # set to `id` from command output above
HEROKU_OAUTH_SECRET= # set to `secret` from command output above
COOKIE_SECRET=change-me
EOF
$ bundle install
$ foreman start
$ open http://localhost:5000
```

## Platform Installation

```
$ heroku create oauth-example-ruby-$USER
$ heroku plugins:install heroku-cli-oauth
$ heroku clients:create -s "Ruby OAuth Example ($USER)" https://oauth-example-ruby-$USER.herokuapp.com
$ heroku config:add HEROKU_OAUTH_ID=     # set to `id` from command output above
$ heroku config:add HEROKU_OAUTH_SECRET= # set to `secret` from command output above
$ heroku config:add COOKIE_SECRET=`dd if=/dev/urandom bs=32 count=1 2>/dev/null | openssl base64`
$ git push heroku master
$ open https://oauth-example-ruby-$USER.herokuapp.com
```
