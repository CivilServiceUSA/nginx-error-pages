![Civil Services Logo](https://cdn.civil.services/common/github-logo.png "Civil Services Logo")

Civil Services Nginx Error Pages
==

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)](https://raw.githubusercontent.com/CivilServiceUSA/nginx-error-pages/master/LICENSE)  [![GitHub contributors](https://img.shields.io/github/contributors/CivilServiceUSA/nginx-error-pages.svg)](https://github.com/CivilServiceUSA/nginx-error-pages/graphs/contributors)

__Civil Services__ is a collection of tools that make it possible for citizens to be apart of what is happening in their Local, State & Federal Governments.


Demos:
---

* [Error 400](https://cdn.civil.services/nginx-error-pages/error_400.html)
* [Error 401](https://cdn.civil.services/nginx-error-pages/error_401.html)
* [Error 403](https://cdn.civil.services/nginx-error-pages/error_403.html)
* [Error 404](https://cdn.civil.services/nginx-error-pages/error_404.html)
* [Error 500](https://cdn.civil.services/nginx-error-pages/error_500.html)
* [Error 503](https://cdn.civil.services/nginx-error-pages/error_503.html)
* [Error 504](https://cdn.civil.services/nginx-error-pages/error_504.html)


Installation ( Nginx ):
---

I made these for my nginx servers.  Here is how I use them:

```bash
mkdir -p /usr/share/nginx/html/error-pages
cd /usr/share/nginx/html/error-pages
git clone https://github.com/CivilServiceUSA/nginx-error-pages.git .
```

Then we can make the config file:
 
```
sudo nano /etc/nginx/snippets/error-pages.conf
```

and paste in the following 

```
error_page 400 /error_400.html;
error_page 401 /error_401.html;
error_page 403 /error_403.html;
error_page 404 /error_404.html;
error_page 500 /error_500.html;
error_page 503 /error_503.html;
error_page 504 /error_504.html;

location = /error_400.html {
    root /usr/share/nginx/html/error-pages;
    internal;
}
location = /error_401.html {
    root /usr/share/nginx/html/error-pages;
    internal;
}
location = /error_403.html {
    root /usr/share/nginx/html/error-pages;
    internal;
}
location = /error_404.html {
    root /usr/share/nginx/html/error-pages;
    internal;
}
location = /error_500.html {
    root /usr/share/nginx/html/error-pages;
    internal;
}
location = /error_503.html {
    root /usr/share/nginx/html/error-pages;
    internal;
}
location = /error_504.html {
    root /usr/share/nginx/html/error-pages;
    internal;
}
```

Then you can include the file in your websites config file:

```
server {
  
  ...
  
  include snippets/error-pages.conf;

  ...
}
```

Since these are HTML files being delivered to the browser, I went ahead and set them with the correct permissions.

```bash
sudo chmod -R u+rwX,go+rX,go-w /usr/share/nginx/html/error-pages
sudo chown -R $USER:$USER /usr/share/nginx/html/error-pages
```