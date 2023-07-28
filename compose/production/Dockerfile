FROM hacklab/mapasculturais:v5.7.1

COPY compose/common/config.php /var/www/html/protected/application/conf/config.php
COPY compose/common/config.d /var/www/html/protected/application/conf/conf-common.d
COPY compose/production/config.d /var/www/html/protected/application/conf/config.d

COPY themes /var/www/html/protected/application/themes
COPY plugins /var/www/html/protected/application/plugins

WORKDIR /var/www/src

# RUN npx pnpm@6 install --global pnpm@6

# RUN npm i -g jake

# RUN pwd
# RUN pnpm install --recursive && pnpm run build

RUN chown -R www-data:www-data /var/www/html
RUN chown -R www-data:www-data /var/www/src

WORKDIR /var/www/html