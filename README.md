This is sample application from Rails book
==========================================
This application comes from Czech translation of the book "Agile Web development with Rails".

Original Czech Book and code Source is available on http://knihy.cpress.cz/ruby-on-rails.html (click on "Soubory ke stažení" to get source).

Use on your own risk.

Tested on Ubuntu:

	lsb_release -a
	No LSB modules are available.
	Distributor ID:	Ubuntu
	Description:	Ubuntu 12.04.4 LTS
	Release:	12.04
	Codename:	precise

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

Add to git...

	git init
	git add .
	git commit -m "Initial release"

Run scaffold:

	rails generate scaffold Product title:string description:text \
	 image_url:string price:decimal

Generates error:

	runtimes.rb:22: syntax error

Solution: install ruby 1.9
	
	sudo apt-get install ruby1.9.3
	sudo apt-get remove ruby1.8
	ruby -v
	ruby 1.9.3p0 (2011-10-30 revision 33570) [i686-linux]
	sudo apt-get remove ruby1.8-dev
	# dangerous! - remove references to old rails/bundle etc...
	sudo rm /usr/local/bin/*
	# install rails again - for ruby 1.9.3
	sudo gem install rails -v 3.2.19

Again install bundle

	bundle install # sudo will prompt for your password

And finally(?) scaffold:


	rails generate scaffold Product title:string description:text \
	 image_url:string price:decimal

Oooopss again:

	Could not find a JavaScript runtime. See https://github.com/sstephenson/execjs for a list of available runtimes. (ExecJS::RuntimeUnavailable)

So install TheRubyRacer:

	sudo gem install therubyracer

Added to github:

	git remote add origin git@github.com:hpaluch/depot.git
	...
	git push -u origin master	

And finally finally scaffold:

	rails generate scaffold Product title:string description:text \
	 image_url:string price:decimal
	Could not find a JavaScript runtime. See https://github.com/sstephenson/execjs for a list of available runtimes. (ExecJS::RuntimeUnavailable)

What? Aarrrrgh!

	sudo apt-get install nodejs


	rails generate scaffold Product title:string description:text \
	 image_url:string price:decimal

Yeah! Done.

Added two decimals to price in file db/migrate/20140816162054_create_products.rb. See diff at https://github.com/hpaluch/depot/commit/583fc6a3ab67f1ba93b48dd955404bf5030e27f1#diff-1

Synchronize db:

	rake db:migrate

Run rails!

	rails server

Go to http://localhost:3000/products

Adjusted textarea, diff on https://github.com/hpaluch/depot/commit/559c66f3f5123b77158fbc5557b2d616c3a50513#diff-1

Finished A1 chapter.



