# Linux-Server-Configuration

#Udacity Project

Digital Ocean Ubuntu instance

IP Address: 159.65.45.137

SSH Port:  2200

Complete URL of the hosted web application: http://159.65.45.137


#Summary of softwares installed and configuration changes made on the server:

Created a Digial Ocean account and created an Ubuntu instance on it.

Accessed the server machine with by using SSH on Git Bash  and logged in as root.

Updated all currently installed packages.

Installed finger.

Created new user account named grader.

Checked the created user account grader using finger

Gave grader the permission to sudo.

Created files named id_rsa and id_rsa.pub containing SSH key pair for grader access using the ssh-keygen tool.

Used the ssh-copy-id script to copy the public key on server.
    
Configured the time zone.

Installed apache and libapache2-mod-wsgi.

Installed PostgreSQL.

Created a new database user with the name catalog.

Created a new database with the name catalog.

Made user catalog the owner of database catalog.

Assigned it with a password.

Installed Git.

Cloned the project from https://github.com/NIKHSR123/Item-Catalog


Made required changes in the create_engine in the files cloned in the application from Git.

# Other Dependencies Installed

python-pip

oauth2client

requests

psycopg2

flask

SQLAlchemy


Finally ran the database setup files to create tables in postgres and fill with sample data.

Modified /etc/apache2/sites-enabled/000-default.conf

  -added
  
    WSGIScriptAlias / /var/www/html/myapp.wsgi 
    
  in the end
  

Modified /var/www/html/myapp.wsgi

  -added
  
    #!/usr/bin/python
    
    import sys
    
    import os
    
    import logging
    
    logging.basicConfig(stream=sys.stderr)
    
    sys.stdout = sys.stderr
    
    sys.path.insert(0,"/home/ubuntu/ItemCatalog/")
    
    os.chdir("/home/ubuntu/ItemCatalog/")
    
    from application import app as application   
    
  in the end


Updated facebook and google auth services with the public ip to allow API access.

Restarted the server

Configured the firewall to only allow incoming connections for SSH(2200), HTTP(80), NTP(123)

Changed the port from 22 to 2200 in /etc/ssh/sshd_config and PermitRootLogin to no and PasswordAuthentication to no.


