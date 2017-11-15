FROM vcatechnology/linux-mint:latest
RUN apt-get update
RUN apt-get install -y apache2 git vim
RUN apt-get clean all


#RUN mkdir /gitrepo
#RUN cd /gitrepo
#RUN git init
#RUN git pull https://github.com/vuejs-templates/simple.git


# Manually set up the apache environment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

# Expose apache.
EXPOSE 80

# Copy this repo into place.
ADD www /var/www/site

# Update the default apache site with the config we created.
ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf

RUN echo 'ServerName localhost' >> /etc/apache2/apache2.conf
# By default start up apache in the foreground, override with /bin/bash for interative.
# todo apache2ctl start
