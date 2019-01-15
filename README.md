# Linux Server Final Project
Linux server final project for Udacity Fullstack nanodegree

## Accessing the site

### Accessing via ssh
IP address : 3.0.175.11

ssh port : 2200

user : grader

 
### Accessing via browser
URL : http://3.0.175.11.nip.io/catalog

## Summary of software installed
1. Python packages: Flask, oauth2client, request, httplib2, sqlalchemy, psycopg2.
2. Database: postgresql
3. For web app: apache2, libapache2-mod-wsgi, libapache2-mod-wsgi-py3

## Configuration changes

### Apache configuration
For configuring Apache created  /etc/apache2/sites-available/catalogApp.conf, with following content:

```html
<VirtualHost *:80>
            ServerName 3.0.175.11.nip.io
            ServerAdmin youemail@email.com
            WSGIScriptAlias / /var/www/catalogApp/catalogApp/catalogApp.wsgi
            <Directory /var/www/catalogApp/catalogApp/>
                    Order allow,deny
                    Allow from all
            </Directory>
            Alias /static /var/www/catalogApp/catalogApp/static
            <Directory /var/www/catalogApp/catalogApp/static/>
                    Order allow,deny
                    Allow from all
            </Directory>
            Alias /templates /var/www/catalogApp/catalogApp/templates
            <Directory /var/www/catalogApp/catalogApp/templates/>
                    Order allow,deny
                    Allow from all
            </Directory>
            ErrorLog ${APACHE_LOG_DIR}/error.log
            LogLevel warn
            CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

All the files related to catalog project reside in folder /var/www/catalogApp/catalogApp/ .

To enable this conf ran following command:

`$sudo a2ensite catalogApp.conf`

### PostgresSQL configuration

1. Added a user for grader.
2. Ran database_setup.py to setup the db and tables.
3. Modified /etc/postgresql/9.5/main/pg_hba.conf file to allow for local db access from any user.

## 3rd party resources used

### Authentication
Using Google openid for authentication & authorization.

### nip.io 
As Google openid requires a proper DNS so using 3.0.175.11.nip.io as redirect URI. 

