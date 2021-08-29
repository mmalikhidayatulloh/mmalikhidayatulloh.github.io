* toc
{:toc}

# Edit file index.html

Masukkan kode berikut dalam tag `<body>....</body>`

```
<form method="post" action="process.php">
Name : <input type="text" name="user_name" placeholder="Enter Your Name" /><br />
Email : <input type="email" name="user_email" placeholder="Enter Your Email" /><br />
Message : <textarea name="user_text"></textarea><br />
<input type="submit" value="Submit" />
</form>
```

# Set Database

* Masuk ke database

    ```
    # systemctl start mariadb
    # mysql -u root -p 'passwordku'
    ```

* Buat Database

    ```
    MariaDB [(none)]> CREATE DATABASE test;
    MariaDB [(none)]> use test;
    Reading table information for completion of table and column names
    You can turn off this feature to get a quicker startup with -A

    Database changed
    MariaDB [test]>
    ```

* Bikin table

    ```
    CREATE TABLE IF NOT EXISTS `users_data` (
    `id` int(11) NOT NULL,
      `user_name` varchar(60) NOT NULL,
      `user_email` varchar(60) NOT NULL,
      `user_message` text NOT NULL
    )AUTO_INCREMENT=1 ;

    ALTER TABLE `users_data`
     ADD PRIMARY KEY (`id`);

    ALTER TABLE `users_data`
    MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;
    ```

# Buat process.php

```
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {//Check it is comming from a form

	//mysql credentials
	$mysql_host = "localhost";
	$mysql_username = "root";
	$mysql_password = "passwordku";
	$mysql_database = "test";
	
	$u_name = filter_var($_POST["user_name"], FILTER_SANITIZE_STRING); //set PHP variables like this so we can use them anywhere in code below
	$u_email = filter_var($_POST["user_email"], FILTER_SANITIZE_EMAIL);
	$u_text = filter_var($_POST["user_text"], FILTER_SANITIZE_STRING);

	if (empty($u_name)){
		die("Please enter your name");
	}
	if (empty($u_email) || !filter_var($u_email, FILTER_VALIDATE_EMAIL)){
		die("Please enter valid email address");
	}
		
	if (empty($u_text)){
		die("Please enter text");
	}	

	//Open a new connection to the MySQL server
	//see https://www.sanwebe.com/2013/03/basic-php-mysqli-usage for more info
	$mysqli = new mysqli($mysql_host, $mysql_username, $mysql_password, $mysql_database);
	
	//Output any connection error
	if ($mysqli->connect_error) {
		die('Error : ('. $mysqli->connect_errno .') '. $mysqli->connect_error);
	}	
	
	$statement = $mysqli->prepare("INSERT INTO users_data (user_name, user_email, user_message) VALUES(?, ?, ?)"); //prepare sql insert query
	//bind parameters for markers, where (s = string, i = integer, d = double,  b = blob)
	$statement->bind_param('sss', $u_name, $u_email, $u_text); //bind values and execute insert query
	
	if($statement->execute()){
		print "Hello " . $u_name . "!, your message has been saved!";
	}else{
		print $mysqli->error; //show mysql error if any
	}
}
?>
```

# Test

Buka browser

```
http://www.malik.net.id
```

![](/assets/IMG/Screenshot_20210829_234320.png)

Coba input

```
Nama    : test
Email   : test@malik.net.id
Message : test
```

Lihat di database

```
MariaDB [test]> select * from users_data;
+----+-----------+-------------------+--------------+
| id | user_name | user_email        | user_message |
+----+-----------+-------------------+--------------+
|  1 | test      | test@malik.net.id | test         |
+----+-----------+-------------------+--------------+
1 row in set (0.001 sec)
```


# Sumber

[https://www.sanwebe.com/2013/07/creating-simple-form-using-php-and-mysql](https://www.sanwebe.com/2013/07/creating-simple-form-using-php-and-mysql)