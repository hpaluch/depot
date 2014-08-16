This is sample application from Rails book
==========================================

On Ubuntu prepare:

	sudo apg-get install rubygems ruby-sqlite3 libsqlite3-dev
	# do not install rails.deb (contains old 2.3 version)
	sudo gem install rails -v 3.2.19

Log of commands to make sample application
------------------------------------------

	rails new depot
	cd depot

correct missing libsqlite3-dev

	sudo apg-get install libsqlite3-dev

rerun bundle install

	bundle install
	git init
	git add .
	git commit -m "Initial release"
	rails generate scaffold Product title:string description:text \
	 image_url:string price:decimal

generates:

	runtimes.rb:22: syntax error

solution: install ruby 1.9
	
	sudo apt-get install ruby1.9.3
	sudo apt-get remove ruby1.8
	ruby -v
	ruby 1.9.3p0 (2011-10-30 revision 33570) [i686-linux]
	sudo apt-get remove ruby1.8-dev
	# dangerous! - remove references to old bundle etc...
	sudo rm /usr/local/bin/*
	# install rails again - for ruby 1.9.3
	sudo gem install rails -v 3.2.19

install bundle again:


