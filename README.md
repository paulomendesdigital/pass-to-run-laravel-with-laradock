# PASS TO RUN LARAVEL WITH LARADOCK

Go to laravel project folder

```console
cd path/to/laravel/project
```

Change the permition of the `storage` and `bootstrap/cache`

```
sudo chmod 777 storage

sudo chmod 777 bootstrap/cache
```

Clone the laradock repository in github

```console
git clone https://github.com/laradock/laradock.git
```

Enter in laradock folder

```console
cd laradock
```

Copy the `env-example` file with name `.env`

```console
cp env-example .env
```

In `.env` file change the `COMPOSE_PROJECT_NAME`, `NGINX_HOST_HTTP_PORT`, `MYSQL_PORT`, `WORKSPACE_SSH_PORT` like below

```
COMPOSE_PROJECT_NAME=laradock
to
COMPOSE_PROJECT_NAME=PROJEC_NAME


*NOTE: PROJEC_NAME must be the name of a phoject. Example: company


---------------------------------------------------------------------------


NGINX_HOST_HTTP_PORT=80
to
NGINX_HOST_HTTP_PORT=EXAMPLE_PORT


*NOTE: EXAMPLE_PORT must be a number of a port of your choice


---------------------------------------------------------------------------


MYSQL_PORT=3306
to
MYSQL_PORT=EXAMPLE_PORT


*NOTE: EXAMPLE_PORT must be a number of a port of your choice


---------------------------------------------------------------------------


WORKSPACE_SSH_PORT=2222
to
WORKSPACE_SSH_PORT=EXAMPLE_PORT


*NOTE: EXAMPLE_PORT must be a number of a port of your choice
```

Inside laradock folder run the code below to up docker containers

```console
sudo docker-compose up -d nginx mysql
```

To see if the containers is up run the code below

```console
sudo docker-compose ps
```


## Project config

Run the code below to enter in workspace

```console
sudo docker-compose exec --user=laradock workspace bash
```

Install the composer dependencies

```console
composer install
```

Install the node dependencies

```console
npm install
```


## .env configuration

Copy the `.env.example` with name `.env`

```console
cp .env.example .env
```

Gerenate the `APP_KEY`

```console
php artisan key:generate
```

Inside the .env change the `APP_NAME` to the project name

**NOTE: the APP_NAME will be displayed in the title of page in the browser**

```
APP_NAME=Laravel
to
APP_NAME='Project Name'
```

Configure mysql with the info below

```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=DATABASE_NAME
DB_USERNAME=root
DB_PASSWORD=root


*NOTE: DATABASE_NAME must be the name of data base that you choose
```

Configure MAIL with the info below

```
MAIL_DRIVER=smtp
MAIL_HOST=HOST_FROM_SENDER
MAIL_PORT=PORT_FROM_SENDER_HOST
MAIL_USERNAME=USERNAME_FROM_SENDER_MAIL
MAIL_PASSWORD=PASSWORD_FROM_SENDER_MAIL
MAIL_FROM_NAME=COMPANY_NAME
MAIL_ENCRYPTION=ENCRYPTION_FROM_HOST
MAIL_CONTACT_ADDRESS=MAIL_THAT_WILL_RECIVE_THE_CONTACT_MESSAGE
MAIL_COPY_ADDRESS=COPY_MAIL_THAT_WILL_RECIVE_THE_CONTACT_MESSAGE


*NOTE: COMPANY_NAME must be the company name. Example: 'Company X'

*NOTE: ENCRYPTION_FROM_HOST must be the encryption from host. Example: ssl, tls

*NOTE2: the MAIL_THAT_WILL_RECIVE_THE_CONTACT_MESSAGE must be the mail tha will recive the contact message: Example: 'mail@mail.com'

*NOTE3: COPY_MAIL_THAT_WILL_RECIVE_THE_CONTACT_MESSAGE must be the mail tha will copied in the contact message
```


## DB

Create the database tables with the code below

```console
php artisan migrate
```
