## Membuat Server IoT menggunakan mosquitto + Node-Red + MySQL dan Grafana

## Prerequisites 
* Instalasi dilakukan pada OS Linux Mint (ARM6 64/ARMv7/ARMv6/X64)

## Requirement 
* install mysql
* install MQTT
* install Node-Red
* install Grafana

## Install tool & library
* Update & upgrade ubuntu
* $ sudo apt-get update && sudo apt-get upgrade -y

## Install mosquitto
* sudo apt-get install mosquitto mosquitto-clients

# Test Mosquito 
* Subscribe dengan topic test,
* $ mosquitto_sub -h localhost -t test

* buka terminal baru untuk publish message Hello world ! pada topic test, 
* $ mosquitto_pub -h localhost -t test -m "hello world!"

## Install MySQL
* install MySQL database,
* $ sudo apt-get install mysql-server

* Jika tidak ditemukan package tersebut, install mariadb-server,
* $ sudo apt-get install mariadb-server

* Jalankan perintah berikut untuk mengatur ulang pasword mysql database, 
* $ sudo mysql_secure_installation

* Setelah itu test mysql dengan cara berikut,
* $ sudo mysql -u root -p

* Masukkan pasword mysql yang kita gunakan 
* Selanjunya kita akan buat user baru pada mysql, ganti 'password' dengan password yang diinginkan,

* >CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';

* Ganti privilages kedalam user baru, 
* > GRANT ALL PRIVILEGES ON * . * TO 'user'@'localhost';

* Reload privileges,
* > FLUSH PRIVILEGES;

* Exit mysql, dan coba lagi akses mysql menggunakan user yang baru,
* $ mysql -u user -p

##  Install NodeJs
* Install NodeJS, jalankan pada terminal,
* $ sudo apt install nodejs

* Install NPM, jalankan pada terminal,
* $ sudo apt install npm

* Check NodeJS & NPM,
* $ nodejs -v
* $ npm -v

## Install Node-red
* Install Node Red via NMP
* $ sudo npm install -g --unsafe-perm node-red node-red-admin

* if you are using linux mint 19.1 and facing a trouble when install node red, teh do this step;
* $ sudo sudo apt update 
* $ sudo apt install snapd
* $ sudo snap install node-red

* Buka browser dan akses URL http://<IP Linux Server>:1880
* 

## Install Grafana (versi 6.7.0)
* Install grafana via.deb package (ARM64/ARMv8/Aarch64) --> RPi 2 B+, 3B, 3B+, 4
* $ sudo apt-get install -y adduser libfontconfig1
* $ wget https://dl.grafana.com/oss/release/grafana_6.7.0_arm64.deb
* $ sudo dpkg -i grafana_6.7.0_arm64.deb

* Install grafana via .deb package (x64)
* $ sudo apt-get install -y adduser libfontconfig1
* $ wget https://dl.grafana.com/oss/release/grafana_6.7.0_amd64.deb
* $ sudo dpkg -i grafana_6.7.0_amd64.deb

* Start grafana server,
* $ sudo systemctl start grafana-server

* check grafana status, 
* $ sudo systemctl status grafana-server

* Check grafana UI pada URL : httpp://<IP Linux Server>:3000

* Login ke grafana UI dengan menggunakan;
* User name : admin
* Password  : admin

* Setelah itu akan diminta untuk change password
* user name : galaxy
* Password  : **********

## CREATE IoT Server
* Setup Tabel IoT
* masuk ke mysql
* $ sudo mysql -u root -p
* kemudian akan masuk ke data base

* pertama kita akan buat database terlebih dahulu,
* > CREATE DATABASE IOT001;

* Create table dengan skema berikut, (bisa di custom sesuai kebutuhan)
* lihat Note(#1) 

## Setup Nodered as data flow
* Buat flow sesuai kebutuhan 

* Selanjutnya install mysql extension pada NodeRed UI,
* Buat flow untuk subscribe MQTT dan Insert ke MYSQL,

* Untuk mengecekk data pada database,
* > USE IOT001;
* > SELECT * FROM IOT_TRX_DATA;