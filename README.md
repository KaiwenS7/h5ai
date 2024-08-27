# h5ai

[![license][license-img]][github] [![web][web-img]][web] [![github][github-img]][github]

A modern HTTP web server index for Apache httpd, lighttpd, and nginx.


## Important

* Do **not** install any files from the `src` folder, they need to be
  preprocessed to work correctly!
* Find a preprocessed package and detailed install instructions on the
  [project page][web].
* For bug reports and feature requests please use [issues][github-issues].


## Build

There are installation ready packages for the latest [releases][release] and
[dev builds][develop]. But to build **h5ai** yourself either `git clone` or
download the repository. From within the root folder run the following
commands to find a fresh zipball in folder `build` (tested on linux only,
requires [`node 10.0+`][node] to be installed, might work on other
configurations).

~~~sh
> npm install
> npm run build
~~~

## Setup

Depends on your server and your apache configs, but this is an example of what you need:

Run the follow commands
~~~sh
> unzip -d /var/www/html/ _h5ai.zip
> sudo apt update
> sudo apt-get install php libapache2-mod-php
> sudo a2enmod mpm_prefork && sudo a2enmod php7.4
> sudo apt-get install php7.4-gd
> sudo apt install imagemagick
~~~

Add the following to Apache SSL-enabled sites-available config:
- DirectoryIndex index.html index.php /_h5ai/public/index.php 

Then
~~~sh
> sudo service apache2 restart
> sudo chgrp www-data /var/www/html/_h5ai/public/cache/
> sudo chgrp www-data /var/www/html/_h5ai/private/cache/
> sudo chmod g+w /var/www/html/_h5ai/private/cache/
> sudo chmod g+w /var/www/html/_h5ai/public/cache/
~~~

That should be it. Check out if you have everything enabled from localhost/_h5ai/public. After that, all web server indexes should be using the files defined by h5ai.

## License

The MIT License (MIT)

Copyright (c) 2020 Lars Jung (https://larsjung.de)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.


## References

**h5ai** profits from other projects, all of them licensed under the MIT license
too. Exceptions are some [Material Design icons][material-design-icons] (CC BY 4.0).


[web]: https://larsjung.de/h5ai/
[github]: https://github.com/lrsjng/h5ai
[github-issues]: https://github.com/lrsjng/h5ai/issues
[release]: https://release.larsjung.de/h5ai/
[develop]: https://release.larsjung.de/h5ai/develop/
[node]: https://nodejs.org
[material-design-icons]: https://github.com/google/material-design-icons

[license-img]: https://img.shields.io/badge/license-MIT-a0a060.svg?style=flat-square
[web-img]: https://img.shields.io/badge/web-larsjung.de/h5ai-a0a060.svg?style=flat-square
[github-img]: https://img.shields.io/badge/github-lrsjng/h5ai-a0a060.svg?style=flat-square
