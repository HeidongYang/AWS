#!/bin/bash
# Use this for your user data(script from top to botom)
# install nginx(Ubuntu)
sudo apt -y update && sudo apt -y upgrade
sudo apt install -y nginx
sudo systemctl start nginx
sudo systemctl enable nginx
sudo chmod 777 index.nginx-debian.html
sudo echo "<h1>Hello World From $(hostname -f)</h1>" > /var/www/html/index.nginx-debian.html
sudo chmod 644 index.nginx-debian.html