MySQL Backup
============

Copy bash Scripts in the remote server to handle mysql databases dumps

Script name | Description
---------|-----------------------------
mysqldump.sh | generate DB dumps. to be added in the crontab
backup_check.sh | Check wether the dumps are generated successfuly, the database name is passed as the first argument

Role Variables
--------------

Variable | Default value |Description
---------|---------------|--------------
mysql_backup_dbuser  | root | the MySQL user used for backup
mysql_backup_dbpass   |  | the password of the backup MySQL user
mysql_backup_nopass | true | whether the password is used or not
mysql_backup_script_user | admin | the user that will execute the backup script
mysql_backup_enabled | yes | wether the dump is enabled or not
mysql_backup_dir     | /srv/mysql/backup | the directory in witch the ddump files will be generated
mysql_backup_retention_days | 3 | Dump retention days
mysql_backup_dump_options | --opt --single-transaction |MySQL dump command options
mysql_backup_db_names | [] | List of database names that will be backuped when this is not set, a dump will be generated for all the databases
mysql_backup_skip_databases |  | a list of databases to be skiped if the mysql_backup_db_names is not specified

Example Playbook
----------------

    - hosts: dbservers
      roles:
         - { role: mysql-backup }

License
-------

BSD
