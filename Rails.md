# Ruby on Rails

## UTF-8 strings

    "þ".mb_chars.capitalize.to_s #=> Þ
	
## Ruby 1.9 file's encoding

Add one of the following to the top of the file

    # encoding: UTF-8

    # coding: UTF-8

    # -*- coding: UTF-8 -*-
    
## BigInt

* http://snippets.dzone.com/posts/show/4422
* http://stackoverflow.com/questions/1066340/how-to-use-long-id-in-rails-applications
* http://svn.northpub.com/plugins/mysql_bigint/lib/mysql_bigint.rb

If you want to change every native database type, put this into initializer or environment.rb

    class ActiveRecord::ConnectionAdapters::MysqlAdapter
      def native_database_types #:nodoc:
        {
          :primary_key => "bigint DEFAULT NULL auto_increment PRIMARY KEY",
          :int64       => { :name => "bigint" },
          :string      => { :name => "varchar", :limit => 255 },
          :text        => { :name => "text" },
          :integer     => { :name => "int", :limit => 11 },
          :float       => { :name => "float" },
          :decimal     => { :name => "decimal" },
          :datetime    => { :name => "datetime" },
          :timestamp   => { :name => "datetime" },
          :time        => { :name => "time" },
          :date        => { :name => "date" },
          :binary      => { :name => "blob" },
          :boolean     => { :name => "tinyint", :limit => 1 },
        }
      end
    end

Good way for Rails 3 (http://blog.hasmanythrough.com/2011/6/1/limitless-strings-for-postgresql) inside application.rb

    initializer "mysql.no_default_string_limit" do
      ActiveSupport.on_load(:active_record) do
        ActiveRecord::ConnectionAdapters::MysqlAdapter::NATIVE_DATABASE_TYPES[:primay_key] = "bigint DEFAULT NULL auto_increment PRIMARY KEY"
      end
    end

Another way (http://stackoverflow.com/questions/3097368/in-rails-activerecord-3-how-do-i-change-the-default-primary-key-type-for-mysql)

    require 'active_record/connection_adapters/mysql_adapter'
    ActiveRecord::ConnectionAdapters::MysqlAdapter::NATIVE_DATABASE_TYPES[:primary_key] = "BIGINT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY".freeze

Yet another (https://gist.github.com/1095974) for environment.rb

    # Load the rails application
    require File.expand_path('../application', __FILE__)

    require 'active_record/connection_adapters/mysql2_adapter'
    require 'active_record/connection_adapters/postgresql_adapter'

    ActiveRecord::ConnectionAdapters::Mysql2Adapter::NATIVE_DATABASE_TYPES[:big_primary_key] = "BIGINT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY".freeze
    ActiveRecord::ConnectionAdapters::PostgreSQLAdapter::NATIVE_DATABASE_TYPES[:big_primary_key] = "bigserial primary key".freeze

    # Initialize the rails application
    Ou1::Application.initialize!
    
