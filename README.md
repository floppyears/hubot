# hubot

hubot is a chat bot built on the [Hubot][hubot] framework.
This one is used by the ECS department at OSU and was
initially generated by [generator-hubot][generator-hubot].
You can run it locally for quick testing,
deploy it to [heroku][],
deploy it to a server with [ansible][ansible-hubot],
or even spin up a virtual machine with [vagrant][vagrant-hubot].

[heroku]: http://www.heroku.com
[hubot]: http://hubot.github.com
[generator-hubot]: https://github.com/github/generator-hubot
[ansible-hubot]: https://github.com/osu-mist/ansible-hubot
[vagrant-hubot]: https://www.vagrantup.com/

### Running hubot Locally

You can test your hubot by running the following, however some plugins will not
behave as expected unless the [environment variables](#configuration) they rely
upon have been set.

You can start hubot locally by running:

    % bin/hubot

You'll see some start up output and a prompt:

    hubot>

Then you can interact with hubot by typing `hubot help`.

    hubot> hubot help
    hubot animate me <query> - The same thing as `image me`, except adds [snip]
    hubot help - Displays all of the help commands that hubot knows about.
    ...

### Configuration

A few scripts (including some installed by default) require environment
variables to be set as a simple form of configuration.

Hubot looks in two files for configuration variables when it is run.
Public configuration variables should be added to [config.env](./config.env).
Private configuration variables such as login information,
or just overrides to the default configuration should be put in `local.env`.

To find documentation for hubot's configuration variables, look in the scripts.
Each script should have a commented header which contains a "Configuration"
section that explains which values it requires to be placed in which variable.

### Scripting

An example script is included at `scripts/example.coffee`, so check it out to
get started, along with the [Scripting Guide][scripting-docs].

For many common tasks, there's a good chance someone has already one to do just
the thing.

[scripting-docs]: https://github.com/github/hubot/blob/master/docs/scripting.md

### external-scripts

There will inevitably be functionality that everyone will want. Instead of
writing it yourself, you can use existing plugins.

Hubot is able to load plugins from third-party `npm` packages. This is the
recommended way to add functionality to your hubot. You can get a list of
available hubot plugins on [npmjs.com][npmjs] or by using `npm search`:

    % npm search hubot-scripts panda
    NAME             DESCRIPTION                        AUTHOR DATE       VERSION KEYWORDS
    hubot-pandapanda a hubot script for panda responses =missu 2014-11-30 0.9.2   hubot hubot-scripts panda
    ...


To use a package, check the package's documentation, but in general it is:

1. Use `npm install --save` to add the package to `package.json` and install it
2. Add the package name to `external-scripts.json` as a double quoted string

You can review `external-scripts.json` to see what is included by default.

[npmjs]: https://npmjs.com/

##  Persistence

Our hubot is configured to use persist its brain to a file with the 
`jobot-brain-file` package.

You can also use the `hubot-redis-brain` package to store hubot's brain in redis.

## Adapters

Adapters are the interface to the service you want your hubot to run on, such
as HipChat or IRC. There are a number of third party adapters that the
community have contributed. Check [Hubot Adapters][hubot-adapters] for the
available ones.

If you would like to run an adapter other than `shell` you will need to add
the adapter package as a dependency to the `package.json` file in the
`dependencies` section.

Once you've added the dependency with `npm install --save` to install it you
can then run hubot with the adapter.

    % bin/hubot -a <adapter>

Where `<adapter>` is the name of your adapter without the `hubot-` prefix.

Most adapters require additional configuration to tell them which server
or account to connect to.

[hubot-adapters]: https://github.com/github/hubot/blob/master/docs/adapters.md

## Deployment

### Local

For testing changes before you push them, you can just run hubot locally
by running `./bin/hubot` as explained above.

### Ansible

Use our [ansible-hubot][] role to deploy hubot to a server.

### Heroku

Detailed documentation for deploying to heroku can be found in the
[hubot documentation][deploy-heroku].

[ansible-hubot]: https://github.com/osu-mist/ansible-hubot
[deploy-heroku]: https://github.com/github/hubot/blob/master/docs/deploying/heroku.md

