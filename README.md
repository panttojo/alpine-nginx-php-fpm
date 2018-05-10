# alpine-nginx-php-fpm
Server with NGINX + PHP 7.1.16. php-fpm based on Alpine Linux


Requirements:
Install docker: https://docs.docker.com/install/

## Build image

```bash
docker build -t alpine-nginx:0.01 .
```

## Run the container

To simply run the container:

```bash
docker run -d -p 8080:80 alpine-nginx:0.01
```

Test  the container:

```bash
curl http://localhost:8080/
```

## Volumes

### Website directory
If you want to link to your web site directory on the docker host to the container run:

```bash
docker run --name alpine-nginx -p 8080:80 -v /public:/var/www/html -d alpine-nginx:0.01
```


## NGINX forbiden
If you have problems with nginx permissions ("/var/www/html/index.php" is forbidden (13: Permission denied))

Try:

```bash
docker exec -ti alpine-nginx bash
chown -R nginx:nginx /var/www/html/
```