
## Kitematic
https://kitematic.com/

## Docker UI

https://www.centos.bz/2016/11/manage-docker-using-ui-for-docker-web-panel/

### 安装教程

```
docker pull uifd/ui-for-docker

docker run -it -d --name docker-web -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock docker.io/uifd/ui-for-docker

```

## Portainer
https://www.linuxidc.com/Linux/2018-03/151307.htm

### 安装教程

```shell
 docker pull portainer/portainer

 docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
```
