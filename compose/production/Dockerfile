FROM hacklab/mapasculturais:latest

COPY compose/common/config.php /var/www/html/protected/application/conf/config.php
COPY compose/common/config.d /var/www/html/protected/application/conf/conf-common.d
COPY compose/production/config.d /var/www/html/protected/application/conf/config.d

COPY themes /var/www/html/protected/application/themes
COPY plugins /var/www/html/protected/application/plugins

RUN chown -R www-data:www-data /var/www/html
RUN chown -R www-data:www-data /var/www/src

WORKDIR /var/www/src

# RUN pnpm install --recursive && pnpm run build 

RUN curl -fsSL https://get.pnpm.io/install.sh | bash -
RUN export PNPM_HOME=/root/.local/share/pnpm
RUN export PATH=$PATH:/root/.local/share/pnpm

RUN /root/.local/share/pnpm/pnpm config set script-shell "/usr/bin/bash"

RUN /root/.local/share/pnpm/pnpm install --recursive
RUN /root/.local/share/pnpm/pnpm run build

WORKDIR /var/www/html