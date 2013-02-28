require "bundler/gem_tasks"
Bundler.require

namespace :db do
  desc "Run migrations"
  task :migrate => [:setup] do
    Sequel::Migrator.run(@database, "db/migrations")
  end

  desc "Reset database"
  task :reset => [:setup] do
    Sequel::Migrator.run(@database, "db/migrations", :target => 0)
    Sequel::Migrator.run(@database, "db/migrations")
  end

  task :setup do
    Sequel.extension :migration

    if ENV["TRAFFIC_SPY_ENV"] == "test"
      database_file = 'db/traffic_spy-test.sqlite3'
      @database = Sequel.sqlite database_file
    else
      @database = Sequel.postgres "traffic_spy"
    end

  end
end

# THIS SPACE RESERVED FOR EVALUATIONS
#
#
#
#
# THIS SPACE RESERVED FOR EVALUATIONS