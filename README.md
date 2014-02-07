Description
===========

A Chef Exception & Reporting Handler for 37signal's 
[Campfire](http://www.campfirenow.com).

Usage
=====

1. Create a 37signals [Campfire](http://www.campfirenow.com) account.
2. Retrieve your Campfire Token. URL TK
3. Create a Campfire Room. URL TK
4. Download the [chef_handler](http://community.opscode.com/cookbooks/chef_handler)
Cookbook.
5. Given you've retrieved your Campfire Token as **TOKEN**, your Room ID NUMBER as 
**ROOM** and Subdomain as **SUBDOMAIN**, add a Recipe similar to the example 
below:

Note this works with [chef 11.10](http://docs.opscode.com/release_notes.html#release-notes-chef-client-11-10-0)

```ruby
include_recipe 'chef_handler'

chef_gem "chef-handler-campfire" do
  action :install
end

chef_handler 'Chef::Handler::Campfire' do
  action :enable
  arguments [ 'SUBDOMAIN', 'TOKEN' , 'ROOM' ]
  source File.join(Gem.all_load_paths.grep(/chef-handler-campfire/).first,
                   'chef', 'handler', 'campfire.rb')
end
```

Also if you are having trouble figuring out the **ROOM** number, it's the number in the URL on your campfirenow.com address.

See also: [Chef Handlers](http://docs.opscode.com/essentials_handlers.html) on the Chef Doc site.


Authors
============
1. [Umang Chouhan](https://github.com/uchouhan) for the campfire gem.
2. [Brain Scott](https://github.com/bscott) for the original campfire_handler gem.
3. [Greg Albrecht](https://github.com/ampledata) for chef-handler-campfire gem.

Contributor
============
1. [JJ Asghar](http://github.com/jjasghar) for updating README.md


Copyright
=========
Copyright 2012 Splunk, Inc.


License
=======
Apache License 2.0
