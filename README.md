# auto-wordpress-deployment
Fully automatic HTTPS WordPress deployment via Docker, LetsEncrypt, and Nginx

## Installation

#### Clone the repository
```shell
git clone https://github.com/chrisrocco/auto-wordpress-deployment/
```

#### Edit `wp.compose.yml`
 - change mysql passwords, making sure they match the environment in the wordpress service
 - change LETSENCRYPT_HOST and VIRTUAL_HOST to your domain name
 - change LETSENCRYPT_EMAIL to your email

#### Optionally change your max upload size
found in `php.ini` and `custom-proxy-settings.conf`

#### Start the servers
```shell
docker-compose -f wp.compose.yml up -d
docker-compose -f proxy.compose.yml up -d
```
Wait a moment for the letsencrypt challenge to finish and you should be good to go
