## Overview 
Initial Script to create Docker Container with Ruby on Rails(7)

## Preview

![screenshot](/previews/preview_1.png?raw=true)

## Requirements

#### [Install Compose](https://docs.docker.com/compose/install/)


## Installation

To clone the sample project, run the following command in your terminal:

```
$ git clone https://github.com/charleseduardome/docker-rails
```

```
$ docker compose run web rails new . --force --database=postgresql
```

Once it's done, you should have generated a fresh app.

List the files.

![screenshot](/previews/preview_2.png?raw=true)



Replace the contents of config/database.yml with the following:

```
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password: password
  pool: 5

development:
  <<: *default
  database: docker-rails_development


test:
  <<: *default
  database: docker-rails_test
```

Now that you’ve got a new Gemfile, you need to build the image, run.

```
$ docker compose up --build
```

Create the database. In another terminal, run:

```
$ docker compose run web rake db:create
```

When finished, fell free to delete `previews` folder, this is not necessary.

Based on this [Documentation](https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/rails/).
