FROM nextcloud:apache

RUN sed -i "s/Components: main/Components: main non-free/" /etc/apt/sources.list.d/debian.sources

RUN set -ex; \
    \
    apt-get update; \
    apt-get install -y \
        ffmpeg intel-media-va-driver-non-free vainfo i965-va-driver \
        ghostscript \
        libmagickcore-6.q16-6-extra \
        procps \
        smbclient \
        supervisor \
		vim cron \
    ; \
    rm -rf /var/lib/apt/lists/* \
# Install & configure Video preview Generator
	echo '/usr/src/nextcloud/occ app:install previewgenerator' > /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
    echo '/usr/src/nextcloud/occ config:system:set enable_previews --value="true"' > /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
    echo '/usr/src/nextcloud/occ config:system:set enabledPreviewProviders 0 --value="OC\\Preview\\Image"' >> /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
    echo '/usr/src/nextcloud/occ config:system:set enabledPreviewProviders 1 --value="OC\\Preview\\Movie"' >> /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
    echo '/usr/src/nextcloud/occ config:system:set enabledPreviewProviders 2 --value="OC\\Preview\\MP3"' >> /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
    echo '/usr/src/nextcloud/occ config:system:set enabledPreviewProviders 3 --value="OC\\Preview\\MKV"' >> /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
    echo '/usr/src/nextcloud/occ config:system:set enabledPreviewProviders 4 --value="OC\\Preview\\MP4"' >> /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
    echo '/usr/src/nextcloud/occ config:system:set enabledPreviewProviders 5 --value="OC\\Preview\\AVI"' >> /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
    echo '/usr/src/nextcloud/occ background:cron' >> /docker-entrypoint-hooks.d/post-installation/setup-preview-generator; \
# Add Crontab for preview generation
	echo "*/10 * * * * /usr/src/nextcloud/occ preview:pre-generate -vvv" >> /var/spool/cron/crontabs/www-data \
        chown www-data /var/spool/cron/crontabs/www-data

RUN mkdir -p \
    /var/log/supervisord \
    /var/run/supervisord \
;

COPY supervisord.conf /

ENV NEXTCLOUD_UPDATE=1
ENV PHP_MEMORY_LIMIT=1024M

ENTRYPOINT ["/usr/bin/supervisord", "-c", "/supervisord.conf"]
