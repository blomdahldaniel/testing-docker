# Testing Docker setup for Laravel Development

## Install project in development

1. Clone this repo and name it oppi `git clone <this repo url> testing-docker`
1. Download, install and launch [Docker Community Edition](https://www.docker.com/community-edition)
1. cd into the project directory `testing-docker`
1. Here you have two choices, if you have composer installed or not: 
  1. If you have composer installed, run `composer install`
  2. If you don't have composer installed you can run it through docker, it will take some time but you at least wont have to install composer. Run `docker run --rm -v $(pwd):/app composer/composer install`. A tip for the future is to make an alias for `alias composerDocker="docker run --rm -v $(pwd):/app composer/composer"` that way you can write only `composerDocker install` etc to use composer this way.
1. Build and run the docker, this will take a couple of minutes depending on bandwidth and computer speed: `docker-compose up` this command will, after installation, be showing a live console from the development server.
1. Migrate and seed the database but first you have to [read more about how it works](#running-commands-on-the-server).. When you know how to run commands on the server: run `php artisan migrate --seed`
1. Access the page by visiting [0.0.0.0](http://0.0.0.0) in your browser.

## Login
Email: admin@admin.com
Pw: 1234
Email: user@user.com
Pw: 1234

## Running commands on the server
For example `php artisan migrate`
To run commands on the server you have to access the server environment.
You can access the server and run commands directly to it by
```
docker-compose exec app <your-commands-here>
```

That means that we can run 
```
docker-compose exec app php artisan migrate
```

If we want to, we can also "login" to the server and use it through the command line freely:
```
docker-compose exec app bash
```
Now you may run any command as if you where on the actual server.

#### Tip!
Add an aliases to make life easier, for example:
```
alias phpd="docker-compose exec app php"
```

So, when you run `phpd artisan migrate` you run it on the server

## Access the database locally
You may access the database through third party program like [Sequel Pro](https://www.sequelpro.com/).

```
Host (värd): 0.0.0.0
Username: oppi
Password: secret
Database: oppi-docker
Port: 33061
```


