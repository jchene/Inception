FROM debian:buster

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y wget php7.3 php7.3-fpm php7.3-mysql mariadb-client
RUN echo ":syntax on\n:set number\n:set tabstop=4\n:set shiftwidth=4\n:set expandtab" > /root/.vimrc

RUN wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
RUN chmod +x wp-cli.phar
RUN mv wp-cli.phar /usr/local/bin/wp

COPY conf/entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
COPY conf/www.conf /etc/php/7.3/fpm/pool.d/www.conf

ENTRYPOINT ["/entrypoint.sh"]
CMD ["/usr/sbin/php-fpm7.3", "-F"]
