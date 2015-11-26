---
title: scaling heroku with php
updated: 2015-11-26
tags: scaling,heroku,php,database with php heroku,apache,nginx
---

>Note: make sure that you visited my pervious tutorial of deploying php project to heroku
http://withintech.com/notes/deploying-heroku-with-php/

Now if you are done with the deploying the app .Here are somethings that you need to do for medium traffic apps.

Selecting the servers . Famous servers that run php are Ngnix and apache . If you need flexibility and support from community
then the apache is best option . If you have to scale your application according to traffic specially with heroku then go with nginx.

But for a startup I would recommend Ngnix . So how to add specific server to heroku .
Create new file in project resource with file name `Procfile` .

Add this text for deploying apache-with-php

```
web: vendor/bin/heroku-php-apache2
```

Deploying with nginx
 
```
web: vendor/bin/heroku-php-nginx
```

Deploying hhvm-apache2

```
web: vendor/bin/heroku-hhvm-apache2
```

Depoyling hhvm-ngnix

```
web: vendor/bin/heroku-hhvm-ngnix
```

Once you added this files . Now you should deploy the current settings to heroku.
Add the files to git

```
prashanth$git add .
```

Commit new push

```
prashanth$git commit -am "pushing procfile"
```

Deploying settings to heroku

```
prashanth$git push heroku master
```
