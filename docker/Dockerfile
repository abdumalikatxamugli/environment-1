FROM debian:stable
RUN apt update
RUN apt install software-properties-common ca-certificates lsb-release apt-transport-https -y
RUN apt install wget -y
RUN apt install gnupg -y
RUN sh -c 'echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
RUN wget -qO - https://packages.sury.org/php/apt.gpg | apt-key add - 
RUN apt-get update
RUN apt-get install php -y
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer
RUN apt-get install php-curl -y
RUN apt-get install php-xml -y
RUN apt-get install php-zip -y
RUN apt-get install curl
ENTRYPOINT ["tail", "-f", "/dev/null"]
#ENTRYPOINT ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]