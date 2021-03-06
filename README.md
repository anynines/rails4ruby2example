## rails4ruby2example

### Reference Application

A simple Rails 4 app using Ruby 2.0.0 to test deployments on [anyines.com](http://anyines.com).

### Install Codebase

Clone the git repository

    $ git clone git@github.com:anynines/rails4ruby2example.git
    $ cd rails4ruby2example
    $ bundle

Create a database and run migrations

    $ rake db:create db:migrate

Run the ```rails server```

    $ rails s

### View Application

From a web browser access the site via [localhost:3000](http://localhost:3000)

## Deploy the application to anynines

### Service dependencies

* PostgreSQL

### Ruby cli (v5)

Install the a9s gem

    $ gem install a9s

Edit the deployment manifest

    $ cp manifest.yml.v5 manifest.yml
    $ vim manifest.yml -> exchange all occurences of your_app_name with your desired application identifier

The https://github.com/cloudfoundry/heroku-buildpack-ruby.git buildpack is referenced within the provided ```manifest.yml.v5```. This buildpack is needed to support Rails 4 and Ruby 2.

Deploy the application

    $ cf push

Visit the application url: http://your_app_name.de.a9sapp.eu .

### Go cli (v6)

Install the cf go cli: https://github.com/cloudfoundry/cli/releases

Edit the deployment manifest

    $ cp manifest.yml.v6 manifest.yml
    $ vim manifest.yml # exchange all occurences of your_app_name with your desired application identifier

Create the needed services

    $ cf create-service postgresql Pluto-free postgresql-your_app_name

Deploy the application

    $ cf push

Visit the application url: http://your_app_name.de.a9sapp.eu .

## Test suite

RSpec and Capybara used for Integration and Unit tests

    $ rspec
