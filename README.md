# Welcome to CoronaGo

## Description

Backend app for CoronaGo app.
API documentation here https://documenter.getpostman.com/view/494437/SzYW1z2B

## Requirements

This app currently works with:

* Ruby 2.5.1
* Rails 5.2.x
* PostgreSQL
* Redis

## Installation

### Clone the repository

```shell
git clone https://github.com/arbob/Coronago-backend
cd Coronago-backend
```

### Check your Ruby version

```shell
ruby -v
```

The output should start with something like `ruby 2.5.1`

If not, install the right ruby version using [rbenv](https://github.com/rbenv/rbenv) (it could take a while):

```shell
rbenv install 2.5.1
```

### Install dependencies

Using [Bundler](https://github.com/bundler/bundler) and [Yarn](https://github.com/yarnpkg/yarn):

```shell
bundle && yarn
```

### Set environment variables

Using [Figaro](https://github.com/laserlemon/figaro):

Rename application.yml.local to application.yml in /config directory for local environment.

### Initialize the database

```shell
rails db:setup db:seed
```
### Create data for local environment

```shell
rails development_tasks:seed_dev_data
```

## Run the server

```shell
rails s
```
## Configure new machines

This needs to be run only once when new machines are added, app can be deployed using capistrano for subsequent deployments.

For test environment

```shell
 ansible-playbook ansible/site.yml -i ansible/inventory/qa01 --ask-vault-pass --extra-vars environment_name=qa01
```

For production environment (Don't deploy without admin's approval)
```shell
 ansible-playbook ansible/site.yml -i ansible/inventory/prod --ask-vault-pass --extra-vars environment_name=prod
```

## Deploy


For test environment

```shell
cap qa01 deploy
```

For production environment (Don't deploy without admin's approval)
```shell
cap production deploy
```

