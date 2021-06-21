# docker image:PHP7.4+nginx

```shell
//关闭主机的php-fpm
brew services stop php@7.4
//关闭主机的nginx
brew services stop nginx
```

进入目录后执行命令：

```shell
docker-compose up -d
```

