Install

	heroku addons:add pgbackups:plus

Create a backup

	heroku pgbackups:capture
	or
	heroku pgbackups:capture HEROKU_POSTGRESQL_PINK

Restore

	heroku pgbackups:restore DATABASE b251  
	heroku pgbackups:restore HEROKU_POSTGRESQL_PINK b251       

Import from backup

	$ PGPASSWORD=mypassword pg_dump -Fc --no-acl --no-owner -h myhost -U myuser mydb > mydb.dump
	
	or
	
	$ heroku pgbackups:restore DATABASE 'http://s3.amazonaws.com/.....mydb.dump?authparameters'

Backup Management

	heroku pgbackups

Download backup

	heroku pgbackups:url b004

Delete backup
	
	heroku pgbackups:destroy b003

Check rows

	heroku pg:info --app your_app
