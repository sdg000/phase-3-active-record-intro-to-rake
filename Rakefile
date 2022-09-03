namespace :greeting do 
  desc "log hello to terminal"
  task :hello do
    puts "hello from Rake!"
  end

  desc "log hola to terminal"
  task :hola do
    puts "hola de Rake!"
  end
end

namespace :db do
  desc "migrate changes to your database"

  #task 1 - create students_table
  # STEPs: RUNNING DEPENDENCY TASK (migrate: :environment) to create a students_table
  # migrate-task depends on environment-task 
  # running environment task will load environment file, which contains 
  # Student class and it's methods (Student.create_db) to create a students_table

  task migrate: :environment do
    Student.create_table
  end


  #task 2 - insert records into students_table
  # STEPs: LOADING "seed.rb " file and Executing content to fill "students_table" with dummy text
  # when this task is run, it will run the sql scripts located in "./db/seeds"
 
  task seed: :environment do
    require_relative "./db/seeds"
  end

end

# LOAD ENV-FILE
# running environment task will load environment file, which contains 
# Student class and it's methods (Student.create_db)
# TO ALLOW migrate-task TO EXECUTE methods of Student Class (Student.create_db)

task :environment do
  require_relative "./config/environment"
end


# task 3 - build "pry console" to interact with "Student Class" and "students_table"
# steps  
# building a console with "pry" to allow interaction with "Student Class" and "students_table"

desc "drop into Pry console"
task console: :environment do
  Pry.start
end

#this task is a dependency task, console depends on environment to start or run
# when console is run , you can interact with Student_Class and students_table

# //bundle exec rake console => starts pry terminal / console
# //Student.all  => use Student Class to access all records in students_table

#OUTPUT:
# [[1, "Melissa", "10th"],
#  [2, "April", "10th"],
#  [3, "Luke", "9th"],
#  [4, "Devon", "11th"],
#  [5, "Sarah", "10th"]]