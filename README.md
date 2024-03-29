# Cloud-based web application for Resident data

## End to End execution steps :

**Step1** : Connect to EC2 instance 

* Go to **EC2 Key** folder in the package and open **Gitbash** in this folder because this folder has EC2 Key-pair.

* Run the following command, if necessary, to ensure your key is not publicly viewable.

```
    chmod 400 resident_EC2_keypair.pem
```
* Connect to your instance using its Public DNS:
```
    ssh -i "resident_EC2_keypair.pem" ubuntu@ec2-34-221-91-120.us-west-2.compute.amazonaws.com
```
* Now you will be connected to EC2 server

**Step 2:** Install the packages mentioned below

* To check for any new updates on the EC2 instance. 
```
    sudo apt-get update
```

* For installing Sql-client
```
    sudo apt-get install mysql-client
```

* For installing python and related frameworks

```
    sudo apt-get install python3
    sudo apt-get install python3-pip
    pip3 install pymysql boto3
    pip3 install flask
```


**Step 3** : 
Run the application using the following command
```
    sudo python3 Housing.py
```
Login as administrator using the following credentials

**username : admin**  
**password : adminpassword**

**Step 4** : Enter any resident's data on **'Add resident Information'** page.


**Step 5** : To check the entries in the database we need to connect to mysql from EC2.

For this, repeat step1 in new Gitbash window and run the below command

```
    mysql -h  resident.cwek9hx2daym.us-east-1.rds.amazonaws.com" -u admin -p
```

When prompted, enter the password as ***adminadmin***

check if the data is reflected in mysql database for the table named **"resident"** in database **"resident"**

```sql
    use resident;
    select * from resident;
```


