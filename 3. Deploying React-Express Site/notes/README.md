> PARADIGM: "Open Book Exam" aka Reference module-docs mentality

<br>
<br>

# Project setup

- Docx [steps ](https://github.com/robertbunch/todo-react-express)

1. Create Ubuntu server instance on AWS

2. update the ubuntu server

3. Update A record on go daddy they act as subdomain

```
  sudo apt update
```

4. upgrade the ubuntu server

```
  sudo apt upgrade
```

5. Install apache2 server package

```
  sudo apt install apache2
```

6. Install mysqul-server server package

```
  sudo apt install mysql-server

  (optional:)
  sudo mysql -u root
  exit
```

7. Install node server package

```
  sudo apt install nodejs
  sudo apt install npm
```

# Getting a project from git to ubuntu server

1. go to this location /var/www

```
  cd /var/www
  pwd
  ls
```

2. remove the html-directory

```
  sudo rm -r html/
  ls
```

3. copy the project [link from git ](https://github.com/robertbunch/todo-react-express) ?

```
  https://github.com/robertbunch/todo-react-express.git
```

4. run the cmd to copy project from git to ubuntu server

```
  sudo git clone https://github.com/robertbunch/todo-react-express.git

```

# Backend process

1. go to this location /var/www/todo-react-express/back-end

```
  cd /var/www/todo-react-express/back-end
  pwd
  ls
```

2. run the cmd to install node module

```
  sudo npm install
```

3. run the cmd to install nodemon for debugging

```
  sudo npm install nodemon -g
```

4. run the server

```
  nodemon
```

5. in this location /var/www/todo-react-express/back-end create config-dir

```
  sudo mkdir config
```

6. move to this location /var/www/todo-react-express/back-end/config create a config.js file

```
  sudo touch config.js
```

7. write this inside config file

```
  var config = {
    db:{
      host: '127.0.0.1',
      user: 'x',
      password: 'x',
      database: 'todo'
    }
  }
  module.exports = config
```

7. move to this location /var/www/todo-react-express/back-end and run cmd to start server

```
  nodemon
```

8. config

# Transfer react build folder using filezila-clent

1. Open file zila

- <img src="image%20notes/1%20site%20manager.png" width="700">

2. Fill connection details

- <img src="image%20notes/2%20fill%20detail.png" width="700">
- Host: paste public ip from aws server
- Protocol: SFTP
- Logon Type: key file
- User: ubuntu
- key file: Browse from location

3. click okay

- <img src="image%20notes/3%20click%20okay.png" width="700">

# Generating HTTPS certificate and a VirtualHost

1. run the following cmds

```
  sudo snap install core; sudo snap refresh core
  sudo snap install --classic certbot
  sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

2. go to this dir " /etc/apache2/sites-availabe "

```
  cd /etc/apache2/sites-availabe
```

3. create virtual host

```
  sudo nano joisland.com.conf
```

4. write these line in joisland.com.conf file

```
<VirtualHost *:80>
  ServerName joisland.com
  DocumentRoot /var/www/joisland
  <Directory "/var/www/joisland">
    allow from all
    AllowOverride All
    Order allow,deny
    Options +Indexes
  </Directory>
</VirtualHost>
```

- Exp:

```
++++  listening on port 80  ++++
<VirtualHost *:80>

++++ we are telling apache If someone shows up looking up for this url ++++
  ServerName joisland.com
  DocumentRoot /var/www/joisland

++++  I want apache u to look here in this directory  ++++
  <Directory "/var/www/joisland">

+++ The rest are apache cmd handle by apache +++
    allow from all
    AllowOverride All
    Order allow,deny
    Options +Indexes
  </Directory>
</VirtualHost>
```

5. go to this location " /var/www " then,

- " sudo mv html joisland "
- Exp: move all files inside html-dir to joisland-dir

```
  cd /var/www
  ls
  sudo mv html joisland
  ls
```

6. go to this dir " /etc/apache2/sites-availabe "

```
  cd /etc/apache2/sites-availabe
  ls
```

7. enabling the site

```
  sudo a2ensite joisland.com.conf
  sudo service apache2 reload
```

8. Add new inbound rule for https traffic in ubuntu aws

- <img src="image%20notes/6%20new%20inbound%20rule%20for%20https%20trafic.png" width="700">

9. run cmd for generating new virtual host

```

  sudo certbot --apache
                  OR
  sudo certbot --authenticator standalone --installer apache -d joisland.com --pre-hook "systemctl stop apache2" --post-hook "systemctl start apache2"
```

9.

# Notes

1. What is web server

- 1. Case: It means actual computer hardware in India
- 2. Case: A piece of software that sole job is to handle and manage http traffic
- 3. A system integrated lots of diff. networking piece moving

2. Ports conventions

- 1. port 80 for http traffic
- 2. port 20 for ssh traffic
- 3. port 443 for https traffic
- 4. Open network ports: can be use for any general purpose 8000, 3000, 8080, etc
