---
layout: post
title:      "Project Manager App"
date:       2020-01-27 22:16:05 +0000
permalink:  project_manager_app
---


## Summary
On the journey to becoming a better full stack developer. I decided to learn Ruby. To aggregate all the lessons that I have learned thus far, I took up the challenge of creating a small Sinatra Application to manage projects.

Quick note, this is article does not discuss every step I took to create this app, but I welcome you to review [Project Manager](https://github.com/anahimana/projectmanager).

## Objective

1. Use Sinatra to build the app
The app inherits from Sinatra::Base to create an app with minimum effort.

```ruby
class ApplicationController < Sinatra::Base; end
```
Hint: You should make sure you have `gem 'sinatra'` in your environment.

2. Use ActiveRecord for storing information in a database
Models inherit from ActiveRecord::Base which makes working with my chosen database easy.

```ruby
class User < ActiveRecord::Base; end
```

Hint: You will find `gem 'activerecord', '~> 5.0', '>= 5.0.0.1', :require => 'active_record'` and `gem 'pg'` in my Gemfile.

3. Implement has_many and belongs_to relationships to the models.

```ruby
class User < ActiveRecord::Base
  has_many :projects
end
```
```ruby
class Project < ActiveRecord::Base
  belongs_to :user
end
```

Hint: When you create your migration to create the projects table, make sure to add the foreign key to user_id.

```ruby
class CreateProjects < ActiveRecord::Migration[5.2]
  def change
    create_table :projects do |t|
      t.string :name
      t.text :description
      t.integer :user_id
      t.timestamps
    end
  end
end
```

4. Include user accounts with unique login attribute (username or email)

```ruby
class User < ActiveRecord::Base
  validates :email, uniqueness: true, on: :create
end
```

Added validation to the user model to check against existing objects on create.

5. Ensure that the belongs_to resource has routes for Creating, Reading, Updating and Destroying
Create project route
```ruby
post '/projects' do
    project = current_user.projects.build(params[:project])
    project.save # Save new project
    redirect '/projects'
end
```

Read project route
```ruby
get '/projects/:id' do
  @project = current_user.projects.find_by(id: params[:id])
  erb :"projects/show"
end
```

Update project route
```ruby
put '/projects/:id/edit' do
  project = current_user.projects.find_by(id: params[:id])
  project.update(params[:project])
  redirect "/projects/#{project.id}"
end
```

Delete/Destroy project route
```ruby
delete '/projects/:id/delete' do
  @project = current_user.projects.find_by(id: params[:id])
  @project.destroy
  redirect '/projects'
end
```

6. Ensure that users can't modify content created by other users
All routes are projected with a #logged_in? helper

```ruby
if logged_in?
  # Do something only a logged in user can do, like retrieve only their projects
  @user_projects = current_user.projects
else
  # Go login....
  redirect '/login'
end
```

## Conclusion
I encourage you to explore [Sinatra](http://sinatrarb.com/) and see how easy it is to get up and running.

