# vagrant-rails
## Working with Rails in Vagrant

###Prerequisites
- Virtualbox or some other Vagrant-supported VM software
- Vagrant 

Vagrant will need the berkshelf & omnibus plugins installed

```vagrant plugin install vagrant-omnibus```  

```vagrant plugin install vagrant-berkshelf```

###Install

This will install rbenv/ruby 2.1.5 and rails. Anything beyond that is up to your imagination.

To run this:

1) Clone the repo

2)
``` vagrant up ```

3) 
``` vagrant ssh ```

4)
``` cd /vagrant ```

5)
``` bundle install ```
which will install rails

6) 
To create a new rails app: 
``` bundle exec rails new myapp ```

Although, I like to use:
``` bundle exec rails new myapp --database=postgresql --skip-turbolinks ```

Now you'll have a folder named "myapp" that is your rails project. Alternatively, if working on an existing project, that project could be copied into the working folder. 
