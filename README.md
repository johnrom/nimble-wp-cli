# Nimble WP-CLI

### A Nimble Docker Environment, for WP-CLI

This project is a proof-of-concept for a complete, distributable dev environment for [WP-CLI](http://wp-cli.org/) development. The purpose is to provide a code-first, dependencies-later approach to development, allowing anyone to download the current WP-CLI version, test it, and begin to develop it, without intimate knowledge of the WP-CLI project's dependencies or the environment in which it lives.

_This is for WP-CLI development, not for developing WordPress websites. Proof-of-concept for that may follow._

It provides out-of-the-box support for developing WP-CLI in VS Code, as well as debugging within all PHP dependencies such as PHPUnit, Behat, etc, to support the creation of tests.

This project is built with [nimble](https://github.com/johnrom/nimble), a simple bash script which facilitates creating distributable Docker environments for various technologies, and may support WP websites (like developing client websites), Node and other technologies in the future. The purpose is to allow developers to dive right into the code of various technologies before learning the entire stack.

### What does it need to work?

In order to use Nimble, you will need access to some common technologies like Git, Docker, and Bash. This list may not be complete, since I may already have other dependencies on my devices not listed here. If so, open an issue!

- Docker for Windows (Windows 10 Professional) or Docker for Mac
    - If using Windows, but not Windows 10 Professional or higher, try Docker Toolbox, but things may not work correctly :(
- Git-aware Command Line (Git Bash, Terminal w/ Git installed, or Git installed within Linux or Bash for Ubuntu on Windows)
- An editor w/ PHP debugging and Path Mapping support (supports VS Code out of the box)

### What does Nimble do?

Nimble enables the use of `Nimble Distribution Templates` which are downloaded from GitHub. Running this project will download the following templates:

- an [nginx-proxy](https://github.com/johnrom/nimble-nginx-proxy-template) that supports redirection of urls to Docker containers automagically
- the [nimble-wp-cli-template](https://github.com/johnrom/nimble-nginx-proxy-template), which runs a list of docker containers such as databases, the WP-CLI command, a WP website, and Composer, PHPMyAdmin, and Xdebug

It then concatenates these templates' `common.yml` and `$project.yml` files into a single `docker-common.yml` and `docker-compose.yml` file, which are run using `docker-compose`.

### Should I use administrative privileges?

Admin privileges are needed to fully automate this project by editing your hosts file to point `wp-cli.local` to the docker container. You can skip the admin privileges, but you'll have to edit your `hosts` file by hand.

### Setting up

- Share your drive with `Docker for Mac` or `Docker for Windows`
- Add `~/bin` to your path. This is used to make the script callable via `nimble`.
- Install a PHP Xdebug debugger for your editor of choice.
- Download this repo.
- Open your Git-Aware command line (Admin privileges, if desired) at the root of this repo (e.g., `~/nimble-wp-cli`)
- Run `./_nimble/nimble.sh localize`. This will enable you to run the `nimble` command.
- Run `nimble init wp-cli`.
- Run `nimble up` and play with your new site at `http://wp-cli.local`

### Debugging

Opening your editor to the folder `nimble-wp-cli/sites/wp-cli` will have it ready to debug PHP and set breakpoints. If you use another editor than VS Code, you will have to configure the editor to point the following `server paths -> subdirectories`

- `/var/www/html` -> `www`
- `/app` -> `cli`

You should be ready to hit breakpoints!

### Can I use this template within other Nimble Environments?

Of course! Just run `nimble create wp-cli --template johnrom/nimble-wp-cli-template` and follow the instructions for enabling debugging within the `sites/wp-cli` folder for the site `http://wp-cli.local`.

### Afterthoughts

Some of the Docker technologies used by this project have been deprecated after a year or so. `docker-compose` templates may need to be updated to stop using the `extends` keyword, or we should get together and ask to reimplement `extends` in v3!