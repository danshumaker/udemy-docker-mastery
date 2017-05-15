# create your custom drupal image here, based of official drupal
FROM drupal:8.3

RUN apt-get update && apt-get install -y git \
    && apt-get install mysql-server \
		&& mysql_install_db \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html/themes

RUN git clone --branch 8.x-3.x --single-branch --depth 1 https://git.drupal.org/project/bootstrap.git \
				&& chown -R www-data:www-data bootstrap

# Get a global installation of Drush on the web / drupal container 
RUN php -r "readfile('http://files.drush.org/drush.phar');" > drush && chmod +x drush && mv drush /usr/bin/

#RUN composer global require drush/drush:7.* \
#  && ln -s ~/.composer/vendor/bin/drush /usr/local/bin/drush \
#	  && drush core-status -y \

# This failes because mysql is not a valid command on the server.
#RUN drush si \
#--account-mail dshumaker@phase2technology.com \
#--account-name dan \
#--account-pass dan \
#--db-su=d8 \
#--db-su-pw=d8 \
#--db-url=mysql://d8:d8@mysql/d8 \
#--locale=en-GB  \
#--site-mail dshumaker@phase2technology.com \
#--site-name BAMF -y

WORKDIR /var/www/html
