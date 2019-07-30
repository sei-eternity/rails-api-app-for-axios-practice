# Misk Rails API

## Details

[Heroku Link](https://misk-api-only.herokuapp.com/)

- This is an API only practice app for an Axios lesson.
- This has an `Event` model with `name:string` and `description:string` fields.
- This app allows full CRUD on the Event resource.
- This app also includes the [Faker gem](https://github.com/stympy/faker) to seed the database.

<br>

## To run locally

1. `git clone https://github.com/sei-eternity/rails-api-app-for-axios-practice`
1. `cd`
1. `bundle`
1. `rails db:create db:migrate db:seed`
1. `rails s`

<br>

## Instructions to build from scratch

1. `rails new api-only --api -d postgresql --skip-test`
1. `Gemfile`

   ```ruby
   gem 'faker'
   gem 'rack-cors'
   ```

1. `bundle`
1. `rails g scaffold events name description`
1. `rails db:create db:migrate db:seed`
1. `db/seeds.rb`

   ```ruby
   10.times do
     newEvent = {
       name: Faker::Coffee.unique.blend_name,
       description: Faker::Hipster.sentence(5)
     }

     Event.create(newEvent)
   end
   ```

1. `rails s`

   ![](https://i.imgur.com/zY3AFeh.png)

1. In `config/database.yml`, remove `username` and `password` from `production`
1. `git add -A`
1. `git commit -m 'first commit'`
1. `heroku login`
1. `heroku create <NAME-OF-APP>`
1. `git push heroku master`
1. `heroku run rake db:migrate`
1. `heroku run rake db:seed`

<br>

## Additional Resources

- [Faker Gem](https://github.com/stympy/faker)
- [Rails API](https://guides.rubyonrails.org/api_app.html)
- [Heroku Deploy](https://devcenter.heroku.com/articles/getting-started-with-rails5)
- [CORS: Cross-Origin Resource Sharing](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
- [rack-cors gem](https://github.com/cyu/rack-cors)
