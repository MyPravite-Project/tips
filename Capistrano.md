# Deployment environment path

From [Change PATH environment with Rails and Capistrano](http://www.pastbedti.me/2011/06/change-path-environment-with-rails-and-capistrano/)

    set :default_environment, {
      'PATH' => "/opt/ruby-enterprise/bin/:$PATH"
    }