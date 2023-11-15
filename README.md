# Docker images

## Nextcloud Apache full
based on https://github.com/nextcloud/docker/blob/master/.examples/README.md#full
contains:
- ffmpeg, intel vaapi
- crontab
- `PHP_MEMORY_LIMIT` set to 1GB
- [video preview generation](https://github.com/nextcloud/previewgenerator) app already installed and crontab configured
- vim

**Install**

```
docker pull ghcr.io/dtila/dockers/nexcloud-ha-crontab:latest
```

Configure the nextcloud (as per official documentation) and you will have the Nextcloud Apache & Video preview generation plugin installed

**What is happening underneath**
After you configure nextcloud container, then the script is executed. This configures the Preview Generator following the (this)[https://www.allerstorfer.at/nextcloud-install-preview-generator/] tutorial

