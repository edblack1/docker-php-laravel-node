FROM phpdockerio/php73-fpm:latest
WORKDIR "/application"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update \
    && apt-get -y install sudo \
    && apt-get -y --no-install-recommends install  php7.3-mysql php7.3-pgsql php7.3-sqlite3 php-xdebug php7.3-gd php7.3-odbc php7.3-soap php7.3-xmlrpc php7.3-xsl php7.3-gd \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install git
RUN apt-get update \
    && apt-get -y install git \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install Compose
RUN /bin/bash -l -c "curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer"

# Install Laravel
RUN composer global require laravel/installer

# Install nvm and node
RUN /bin/bash -l -c "curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -"
RUN sudo apt -y install nodejs
#RUN /bin/bash -l -c "curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash"
#RUN /bin/bash -l -c ". ~/.nvm/nvm.sh"
#RUN nvm install 10.16.3