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

1. Clone this repository.

    ```
    git clone git@github.com:asimlqt/docker-pimcore.git
    ```

2. Rename 'docker-compose.override.yml.dist' to 'docker-compose.override.yml'. If you're using OSX then you'll want to change the PHP UID and GID environment variables. You can find out what they are by running `id` in the terminal.

    ```
    cp docker-compose.override.yml.dist docker-compose.override.yml
    ```

3. Open a terminal and cd in to this repository.

    ```
    cd docker-pimcore
    ```

4. Install Pimcore using the composer method described on the Pimcore website. The only difference is that the project-name' will be 'web'. e.g.

    ```
    composer create-project pimcore/pimcore ./web
    ```

5. Start docker using:

    ```
    docker-compose up -d
    ```

6. Open a browser and navigate to 'http://localhost/'. The pimcore installation screen will open up. Enter the following details:
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
Make sure you don't have Apache or MySQL running locally. If you do then stop those services and re-run `docker-compose up -d` or alternaitvely you can run them on different ports by editing the docker-compose.override.yml file. 

##### Error on Pimcore installation screen: var folder must be writable
Just make the var folder writable `sudo chmod -R 777 web/website/var`. This will hopefully be resolved in the future so you don't have to set the permissions. If you set the correct user and group ids in the docker-compose.override.yml file then you shouldn't have this issue.