# Salin kode berikut

```
<?php
$response = '';
if (isset($_POST['email'], $_POST['subject'], $_POST['name'], $_POST['msg'])) {
	if (!filter_var($_POST['email'], FILTER_VALIDATE_EMAIL)) {
		$response = 'Email is not valid!';
	} else if (empty($_POST['email']) || empty($_POST['subject']) || empty($_POST['name']) || empty($_POST['msg'])) {
		$response = 'Please complete all fields!';
	} else {
		$to      = 'contact@example.com';
		$from    = $_POST['email'];
		$subject = $_POST['subject'];
		$message = $_POST['msg'];
		$headers = 'From: ' . $_POST['email'] . "\r\n" . 'Reply-To: ' . $_POST['email'] . "\r\n" . 'X-Mailer: PHP/' . phpversion();
		mail($to, $subject, $message, $headers);
		$response = 'Message sent!';		
	}
}
?>
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width,minimum-scale=1">
		<title>Contact Us</title>
		<style>
		html {
			background-color:#F8F9F9;
			padding:30px;
		}
		input,textarea,select,p {
			outline:0;
			font-family: Tahoma, Geneva, sans-serif;
		}
		.contact input[type="text"], .contact input[type="email"] {
			display: block;
			margin-top: 15px;
			padding: 15px;
			border: 1px solid #dfe0e0;
			width: 500px;
		}
		.contact input[type="text"]:focus, .contact input[type="email"]:focus {
			border: 1px solid #c6c7c7;
		}
		.contact textarea {
			resize: none;
			margin-top: 15px;
			padding: 15px;
			border: 1px solid #dfe0e0;
			width: 700px;
			height: 200px;
		}
		.contact textarea:focus {
			border: 1px solid #c6c7c7;
		}
		.contact input[type="submit"] {
			display: block;
			margin-top: 15px;
			padding: 15px;
			border: 0;
			background-color: #518acb;
			font-weight: bold;
			color: #fff;
			cursor: pointer;
			width: 150px;
		}
		.contact input[type="submit"]:hover {
			background-color: #3670b3;
		}
		</style>
	</head>
	<body>
		<form class="contact" method="post" action="contact.php">
			<input type="email" name="email" placeholder="Your Email Address" required>
			<input type="text" name="name" placeholder="Your Name" required>
			<input type="text" name="subject" placeholder="Subject" required>
			<textarea name="msg" placeholder="What would you like to contact us about?" required></textarea>
			<input type="submit">
		</form>
		<?php if ($response): ?>
		<p><?php echo $response; ?></p>
		<?php endif; ?>
	</body>
</html>
```

# Edit file

Dalam kode di atas alamat email yang dituju masih `contact@example.com`. Silahkan ganti alamat emailnya dengan alamat email anda. Kemudian simpan dengan nama `contact.php`

# Sumber

[https://codeshack.io/how-to-create-contact-page-php/](https://codeshack.io/how-to-create-contact-page-php/)