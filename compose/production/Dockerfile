FROM hacklab/mapasculturais:v5.7.1

COPY compose/common/config.php /var/www/html/protected/application/conf/config.php
COPY compose/common/config.d /var/www/html/protected/application/conf/conf-common.d
COPY compose/production/config.d /var/www/html/protected/application/conf/config.d

COPY themes /var/www/html/protected/application/themes
COPY plugins /var/www/html/protected/application/plugins

WORKDIR /var/www/src /var/www/html/protected/application/themes/BaseV1/assets/vendor/leaflet/lib/leaflet-plugins-updated-2014-07-25

RUN rm -rf Leaflet.label-master
RUN rm -rf Leaflet.markercluster-master

RUN git clone https://github.com/Leaflet/Leaflet.label.git Leaflet.label-master
RUN git clone https://github.com/Leaflet/Leaflet.markercluster Leaflet.markercluster-master

WORKDIR /var/www/src

ENV SHELL=bash
ENV PNPM_HOME=/root/.local/share/pnpm
ENV PATH="/root/.local/share/pnpm:${PATH}"

RUN curl -fsSL https://get.pnpm.io/install.sh | sh -
RUN source /root/.bashrc

RUN npm i -g jake

RUN pnpm install --recursive
RUN pnpm run build

RUN chown -R www-data:www-data /var/www/html
RUN chown -R www-data:www-data /var/www/src

WORKDIR /var/www/html