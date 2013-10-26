task :copy_template do
  sh "cp source/stylesheets/application-template.css.less source/stylesheets/application.css.less", verbose: false
end

desc "Build/compile the site"
task :build => :copy_template do
  sh "bundle exec middleman build --clean"
end

desc "Start the development server"
task :server do
  sh "bundle exec foreman start"
end

