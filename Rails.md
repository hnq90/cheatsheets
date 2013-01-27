## Rails cheatsheet

Ignore the default Unit Test and use PostgreSQL as database

	rails new APPNAME -T -d postgresql
	
Generate:

	rails generate controller CONTROLLERS
	rails generate model MODEL
	
Rake task:

	rake db:create
	rake db:test:prepare
	
	rake db:migrate
	rake db:rollback
	

Email regular expression

	email_regex = /\A[\w+\-.]+@[a-z\d\-.]+\.[a-z]+\z/i
	
Asset compile

	RAILS_ENV=production bundle exec rake assets:precompile
	
.gitignore

	.bundle
	db/*.sqlite3*
	log/*.log
	*.log
	tmp/**/*
	tmp/*
	doc/api
	doc/app
	*.swp
	*~
	.DS_Store

Git commands

	git checkout -b NEW_BRANCH_NAME
	git merge BRANCH_TO_MERGE
	git branch -D BRANCH_TO_DELETE