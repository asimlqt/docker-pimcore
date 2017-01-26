# Pimcore Docker template

This repo prvoides a quick and easy way to get Pimcore running in Docker.

It runs the following Docker containers:

- Nginx (latest)
- PHP 7
- MySQL 5.7
- Memcached

## Requirements

* Docker compose >= 1.7
* Composer

## Installation

1. Download or clone this repository.
2. Open a terminal and cd in to this repository.
3. Install Pimcore using the composer method described on the Pimcore website. The only difference is that the 'project-name' will be 'web'. e.g.
    `composer create-project pimcore/pimcore ./web`
4. Start docker using:
    `docker-compose up -d`
5. Open a browser and navigate to 'http://localhost/'. The pimcore installation screen will open up. Enter the following details:
    - `MySQL Settings`
    - Adapter: Pdo_Mysql
    - Host/Socket: db.docker
    - Port: 3306
    - Username: pimcore
    - Password: pimcore
    - Database: pimcore
    - `Admin Settings`
    - Enter an admin password

## Troubleshooting
##### Error starting service 
Make sure you don't have Apache or MySQL running locally. If you do then stop those services and re-run `docker-compose up -d`

##### Error on Pimcore installation screen: var folder must be writable
Just make the var folder writable `sudo chmod -R 777 web/website/var`. This will hopefully be resolved in the future so you don't have to set the permissions.