---
title: scaling heroku with php
updated: 2015-11-26
tags: scaling,heroku,php,database with php heroku,apache,nginx,dyno's,mysql ,with heroku
---

>Note: make sure that you visited my pervious tutorial of deploying php project to heroku
http://withintech.com/notes/deploying-heroku-with-php/

Now if you are done with the deploying the app .Here is something that you need to do for medium traffic apps.

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

Now you need to know about dyno's

>Web Dynos: Web dynos are dynos of the “web” process type that is defined in your Procfile. Only web dynos receive HTTP traffic from Heroku’s routers.

You can read more about dyno's at [https://devcenter.heroku.com/articles/dynos](https://devcenter.heroku.com/articles/dynos).
There are basically four scalable dyno's

* Free dyno
* Hobby dyno's prefect for blog . Costs about 7$
* Standard 1x/2x . Perfect for startups . Costs about 25$
* Performance -M/L .For high performance  . Costs upto 500$ per single dyno

You select your dyno at [https://dashboard.heroku.com/apps/pramana/resources](https://dashboard.heroku.com/apps/pramana/resources).

###Setting up mysql with heroku


Now you can find addons at [https://elements.heroku.com/addons](https://elements.heroku.com/addons)
Heroku has only two addon's for mysql

* ClearDB
* JawsDB

#### ClearDB
<img src='http://withintech.com/assets/img/heroku2.png'/>

#### JawsDB
<img src='http://withintech.com/assets/img/heroku3.png'/>

#### Adding ClearDB and connecting it .

Connecting clearDB with heroku app

```
heroku addons:create cleardb:ignite
```

plans for cleardb

<img src='http://withintech.com/assets/img/heroku4.png'/>

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- mobile ad -->
<ins class="adsbygoogle"
     style="display:inline-block;width:320px;height:100px"
     data-ad-client="ca-pub-6760357694701522"
     data-ad-slot="9506986493"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

#### Adding jawsDB and connecting it

Connecting jawsDB with heroku app

```
heroku addons:create jawsdb:ignite
```

plans for jawsdb

<img src='http://withintech.com/assets/img/heroku5.png'/>

please follow next tutorial for connecting google-mysql with heroku app [http://withintech.com/notes/heroku-with-google-mysql](http://withintech.com/notes/heroku-with-google-mysql)
Editor : prashanth varma , information security researcher and white hat hacker . Contact me:[prashanthvarmadomma@gmail.com](mailto:prashanthvarmadomma@gmail.com)

<ins class="adsbygoogle"
     style="display:inline-block;width:320px;height:100px"
     data-ad-client="ca-pub-6760357694701522"
     data-ad-slot="9506986493"></ins>
