#!/bin/bash
# Use this for your user data(script from top to botom)
# install nginx(Ubuntu)
sudo apt -y update && sudo apt -y upgrade
sudo apt install -y apache2
sudo systemctl start apache2
sudo systemctl enable apache2
sudo chmod 777 index.html
sudo echo "<h1>Hello World From $(hostname -f)</h1>" > /var/www/html/index.html
sudo chmod 644 index.html
Test