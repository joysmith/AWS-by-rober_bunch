> PARADIGM: "Open Book Exam" aka Reference module-docs mentality

How to use [request module ](https://www.npmjs.com/package/request) ?
<br>
<br>

# Project setup

1. update the ubuntu server

```
  sudo apt update
```

2. upgrade the ubuntu server

```
  sudo apt upgrade
```

3. Install apache2 server package

```
  sudo apt install apache2
```

4. How to test if the apache2 server is running or not

```
  sudo service apache2 status
```

# How to edit DNA A records in godaddy

1. Go to Godaddy dashboard and click on DNS

- <img src="image%20notes/1%20DNS.png" width="700">

2. Edit A record

- <img src="image%20notes/2%20edit%20A%20record.png" width="700">

# About apache2 package structure

1. Where do apache2 server live

```
  cd /etc/apache2/
  pwd
```

2. Where to find html file

```
  cd /var/www/html
  pwd
  ls -l
```

# Getting a project from git to ubuntu server

- <img src="image%20notes/3%20git%20project.png" width="700">

1. go to this location /var/www

```
  cd /var/www
  pwd
  ls
```

2. remove the html directory

```
  sudo rm -r html/
  ls
```

3. copy the project link from git

```
  https://github.com/robertbunch/jquery-todo.git
```

4. run the cmd to copy project from git to ubuntu server

```
  sudo git clone https://github.com/robertbunch/jquery-todo.git html
```

5. Disection of cmd " sudo git clone https://github.com/robertbunch/jquery-todo.git html "

- sudo git clone https://github.com/robertbunch/jquery-todo.git 👉html
- the html there after the git link is telling create a html-director
- and inside of that html-derector paste the project file

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
