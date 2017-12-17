# Owncloud for dokku

How to easily deploy owncloud using [Dokku](http://dokku.viewdocs.io/dokku/).

## Locally


Push to dokku:
```
git remote add dokku dokku@your-server:owncloud
git push dokku master
```

## Remote server

### MariaDB

Install MariaDB plugin:
```
sudo dokku plugin:install https://github.com/dokku/dokku-mariadb.git mariadb
```


Then create a database:
```
dokku mariadb:create owncloudDB
```

Expose database (in the futur, link database with container):
```
dokku mariadb:expose owncloudDB
```


### Volumes



### SSL

Secure your application with Letsencrypt:

Install Letsencrypt plugin:
```
sudo dokku plugin:install https://github.com/dokku/dokku-letsencrypt.git
```

Configure Letsencrypt:
```
dokku config:set --no-restart owncloud DOKKU_LETSENCRYPT_EMAIL=your@email.tld
```

Add certificate:
```
dokku letsencrypt owncloud
```
