Connect to vm
Download application
Install mysql
Configure environment – mysql, python, bash & Azure
Run App

Connect to VM
```bash
sshmyuserid@myvmdns
```

Download Application
```bash
git clone https://github.com/Azure-Samples/azure-voting-app
```

Install mysql
```bash
sudo apt update
sudo apt install mysql-server
sudo systemctl start mysql.service
```
```bash
# login to mysql
sudo mysql -u root -p
[sets password, make a note!!]
```
Configure environment – mysql
```bash
# from mysql>
create user 'azurevote'@'localhost' identified by 'AzureV0te';
grant all privileges on *.* to 'azurevote'@'localhost';
create database azurevote;
use azurevote;
## create table… from azurevote.sql
CREATE TABLE `azurevote`.`azurevote` (`voteid` INT NOT NULL AUTO_INCREMENT,`votevalue` 
VARCHAR(45) NULL,PRIMARY KEY (`voteid`));
# exit mysql
quit
```

Configure environment – python
```bash
# install pip and required python modules
sudo apt install python3-pip
python3 -m pip install flask
python3 -m pip install flask-mysql
```
```bash
# from azure-voting-app/azure-vote/azure-vote
# edit main.py
# change the port to 8080
# comment out the last 2 lines with #
```

Configure environment – bash 
```bash
export MYSQL_USER=azurevote
export MYSQL_PASSWORD=AzureV0te
export MYSQL_DATABASE=azurevote
export MYSQL_HOST='localhost'
```

Configure environment – Azure
```bash
# Goto the Portal and create an 
NSG Inbound Rule to allow TCP 
on destination Port 8080
```
Run App (bash)
```bash
python3 main.py
```
