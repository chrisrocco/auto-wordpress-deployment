# auto-wordpress-deployment
Fully automatic HTTPS WordPress deployment via Docker, LetsEncrypt, and Nginx

##### This setup uses the following projects:
+ https://github.com/jwilder/nginx-proxy
+ https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion

## Installation

#### 1. Clone the repository
```shell
git clone https://github.com/chrisrocco/auto-wordpress-deployment/ wordpress
```

#### 2. Create the external network
```shell
docker network create proxy-net
```

#### 3. Start the Nginx proxy and Letsencrypt services
```shell
docker-compose -f proxy.compose.yml up -d
```

#### 4. Configure and start the WordPress service
##### Edit `wp.compose.yml`
 - change mysql passwords, making sure they match the environment in the wordpress service
 - change LETSENCRYPT_HOST and VIRTUAL_HOST to your domain name
 - change LETSENCRYPT_EMAIL to your email

```shell
docker-compose -f wp.compose.yml up -d
```

_* Note that this doesn't have to be a WordPress app. This setup works for any app._

Wait a moment for the letsencrypt challenge to finish and you're all set!

## Further Configuration

#### Edit Nginx and php.ini Settings
found in `php.ini` and `custom-proxy-settings.conf`

#### Use a remote database service
Just authorize your server's IP, and edit the environment of the WordPress service.

Remove the old MySQL after backing up to save space.

Remove the mysql service from wp.compose.yml