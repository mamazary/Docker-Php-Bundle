# Docker PHP Bundle
Dockerized Simple PHP with apache and some php extension.
I build this docker image for easily run the PHP Framework such as Laravel, so I just make it simple.

This image contain :
 - PHP 7.2
 - Apache
 - PHP Extension 
   - GD
   - mcrypt
   - json
   - xml
   - mbstring
   - tokenizer
   - ctype
   - xml
   - pdo_mysql
   - And more, check ```php -m``` or ```php -i``` for checking the installed extension

You can just easily spin up the container using this image and get the Framework of your choice. 

## Install another extension
This base script is extended from official php, if you want to install other extension that is not provided here, you can use this script ````docker-php-ext-configure````, ````docker-php-ext-install````, and ````docker-php-ext-enable```` or if there no extension found using that method, you can use ```pecl install``` to download and compile it, then use ```docker-php-ext-enable``` to enable it. Be sure to check the official php documentation about the base image here : https://hub.docker.com/_/php

## Change webroot
In some framework, we need to change the webroot, such as public folder or etc. If you want to change the webroot, just using this method.
```
FROM mamazary/php-bundle

ENV APACHE_DOCUMENT_ROOT /path/to/webroot

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf
```

## Contributing

Contributions are very welcome on this repository!
Leave an issue on Github, or create a Pull Request.


## License

This work is under [MIT](LICENSE) license.
