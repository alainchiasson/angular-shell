# The Angular Shell

The script included here is an Angular Shell. While I know that Angular shell does
not exist, this script is a __portable__ angular cli environement, that I can
only describe as a shell.

The __big trick__ is the shell is a simple wrapper script to a docker container
that contains the proper versions on nodeJS, NPM and Yarn - as well as some packages
used by developers to build Angular6 applications.

The main goal is to provide a local command and environment without polluting
a developer machine. This can also help in delivering a standard tool set to
the various developers.

# Installing

The installation is simple - place the script anywhere on the path. The script
is written so it will work on both linux, OSX and Windows 10 - which is why it
looks odd. But it does require that docker be installed - and of course have
access to the excelent docker images [teracy/angular-cli](https://hub.docker.com/r/teracy/angular-cli/) - either on
internet or locally.

# Usage

The usage is very similar to using the commands directly, with the following
exception:

- prefixing everything with `angsh`.
- The docker image mounts the local directory. While this allows things to get
  storred outside the docker image, it also means no references outside the
  directory (but that's a good thing)
- The parameters are passed directly to the container with a check. This is good
  and bad. Bad since you can run any command. Good since also means that
  `angsh /bin/bash` will drop you into a bash shell in the local directory
-  Because it hides the __context switching__ from local command to
   docker command, you may not get what you expect as a result.


## The simple example

Teh following is the same as the example presented at the top of the
[Angular CLI](https://cli.angular.io/) page:

```
# Note @angular/cli is already installed.
angsh new my-dream-app
cd my-dream-app

# the host 0.0.0.0 is required to allow access external to the Docker container.
angsh ng serve --host 0.0.0.0
```

And thats it.
