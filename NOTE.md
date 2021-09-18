## 1
## Create tabel dengan skema berikut (tabel bisa di custom)
## create data base 
CREATE TABLE `IOT001`.`IOT_TRX_DATA` (
    `ID` bigint(11) NOT NULL AUTO_INCREMENT,
    `DATETIME` bigint(16),
    `DEVICEID` varchar(50),
    `LATITUDE` decimal(16,10),
    `LONGITUDE` decimal(16,10),
    `VALUE` decimal(10,6),
    PRIMARY KEY (`ID`)
);

## 2
## CODING UNTUK BLOCK FUNCTION
msg.topic = "INSERT INTO IOT_TRX_DATA (DATETIME, DEVICEID, LATITUDE, LONGITUDE, VALUE)" +
        "VALUES("+ 
        msg.payload.DATETIME + ",'" +
        msg.payload.DEVICEID + "'," +
        msg.payload.LATITUDE + "," +
        msg.payload.LONGITUDE + "," +
        msg.payload.VALUE + ")"
return msg;

## 3
## JSON SAMPLE UNTUK BLOCK INJECT,
{"DATETIME" : 1590714329,"DEVICEID" : "A1500001","LATITUDE" : -6.121435, "LONGITUDE" :106.774124, "VALUE":0.75}


## 4
## That's All only example to make a table and connecting between Json to mysql

