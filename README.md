
Heroku Buildpack: SSH
=====================

Reads and sets ssh private key from an environment variable.  Designed to be used with [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) to allow build process to access private resources without storing unencrypted keys in the repository.


Usage
-----
Set `SSH_KEY` variable to private key:

    heroku config:set SSH_KEY="`cat /path/to/id_rsa`"

The key must not require a password to use.  Before your application is run the `SSH_KEY` environment variable is unset so that it is not so easily accessible.

Enable the multi buildpack:

    heroku config:set BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git

Create `.buildpacks` file:

    https://github.com/${YOUR_NAME}/heroku-buildpack-ssh.git
    ssh://git@github.com:${YOUR_NAME}/top-secret-buildpack.git
    https://github.com/heroku/heroku-buildpack-something-something.git

This buildpack should obviously be loaded before any buildpacks requiring access to private repositories.

It is highly recommended that you use your own fork as updates may break backwards compatibility.

Bugs
----

Please report any bugs to using the [issue tracker](https://github.com/bwhmather/heroku-buildpack-ssh/issues).

Pull requests are welcome.