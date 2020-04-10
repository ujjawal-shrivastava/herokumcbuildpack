# Heroku Minecraft Buildpack

This is a [Heroku Buildpack](https://devcenter.heroku.com/articles/buildpacks)
for running a Minecraft server in a [dyno](https://devcenter.heroku.com/articles/dynos).

For an actual deployment example, please look into [my deployment repository](https://github.com/Chengsong/heroku-mc-deploy).

## Env Variables

### DropBox

The Heroku filesystem is [ephemeral](https://devcenter.heroku.com/articles/dynos#ephemeral-filesystem),
which means files written to the file system will be destroyed when the server is restarted.

You will have to set a DropBox auth token to synchronize your world information with:

```
$ heroku config:set DROPBOX_API_TOKEN="MY_DROPBOX_TOKEN"
```

### ngrok

You need to set a ngrok auth token to open secure tunnel to your minecrfat server:

```
$ heroku config:set NGROK_API_TOKEN="MY_NGROK_TOKEN"
```

You can customize ngrok by setting the `NGROK_OPTS` config variable. For example:

```
$ heroku config:set NGROK_OPTS="-subdomain=my-subdomain"
```

### Minecraft

You can choose the Minecraft version by setting the MC_VERSION like so:

```
$ heroku config:set MC_VERSION="1.10.2"
```

You can also configure the server properties by creating a `server.properties`
file in your project and adding it to Git. This is how you would set things like
Creative mode and Hardcore difficulty. The various options available are
described on the [Minecraft Wiki](http://minecraft.gamepedia.com/Server.properties).

You can add files such as `banned-players.json`, `banned-ips.json`, `ops.json`,
`whitelist.json` to your Git repository and the Minecraft server will pick them up.
