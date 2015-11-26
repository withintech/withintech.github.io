---
title: Deploying your php project with heroku 
updated: 2015-11-26
---
>First of all heroku is a cloud platform that lets companies build, deliver, monitor and scale apps .

There are various platforms or stacks that you can run on heroku . Number of add-ons to scale your application from sending e-mail's to database management . If you have a startup and tight budget to develop an app then heroku is the best platform to develop.

So we are going to disscus about deploying a php project on to heroku .
Create an heroku account at heroku.com and visit this url [https://dashboard.heroku.com/new](https://dashboard.heroku.com/new) you will have something like this
<img src="assets/img/heroku1.png"/>

Enter your app name and you will redirected to the dashboard. 
Before you want to deploy install the heroku toolbelt [https://toolbelt.heroku.com/](https://toolbelt.heroku.com/)
Make sure that you installed `git` too.
Lets get started then . Here is the checklist before deploying

1. create a new app
2. install heroku tool belt
3. install git command line

log in to your heroku account from terminal

```
prashanth$heroku login
```
Now you need to clone the project from heroku if you have to copy source to computer

```
prashanth$heroku git:clone -a YOUR_APP_NAME
```

Otherwise go to your project source and install composer . Add the `composer.json` file to the main source of project

```json
{
    "authors": [
        {  }
    ],
    "require": {
        "php": ">=5.4.0",
        "ext-curl": "*",
        "ext-json": "*"
    },
    "require-dev": {
        "phpunit/phpunit": "~4.0",
        "squizlabs/php_codesniffer": "~1.5"
    },
    "autoload": {
    },
    "extra": {
        "branch-alias": {
            "dev-master": "1.1-dev"
        }
    }
}

```
After that run this command `php composer.phar install` .
Now your app is ready for deploying . You need to connect this project resource to the heroku app.

```
heroku git:remote -a YOUR_APP_NAME
```
Intiate the git after connecting the resource

```
git init
```

Add files to git 

```
git add .
```

Now commit the push to heroku

```
git commit -am "making better"
```

Finally push it to the heroku

```
git push heroku master
```
