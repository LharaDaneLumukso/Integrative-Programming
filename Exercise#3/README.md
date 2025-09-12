<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exercise #3</title>
    <style>
        body {
            min-height: 100vh;
            margin: 0;
            background: linear-gradient(135deg, #e0c3fc 0%, #8ec5fc 100%);
            display: flex;
            align-items: center;
            justify-content: center;
        }
        form {
            background: #fff;
            padding: 32px 28px;
            border-radius: 18px;
            box-shadow: 0 8px 32px rgba(44, 62, 80, 0.15);
            width: 100%;
            max-width: 370px;
        }
        label {
            display: block;
            margin-bottom: 6px;
            color: #333;
            font-size: 1rem;
            font-weight: 600;
        }
        input[type="text"],
        input[type="password"],
        input[type="email"] {
            width: 100%;
            padding: 10px 12px;
            margin-bottom: 18px;
            border: 1px solid #bdbdbd;
            border-radius: 8px;
            font-size: 1rem;
            background: #f9f9f9;
            transition: border 0.2s;
        }
        input[type="text"]:focus,
        input[type="password"]:focus,
        input[type="email"]:focus {
            border: 1.5px solid #8ec5fc;
            outline: none;
        }
        input[type="checkbox"] {
            margin-right: 8px;
        }
        .checkbox-label {
            font-size: 0.97rem;
            color: #555;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
        }
        input[type="submit"] {
            background: linear-gradient(90deg, #8ec5fc 0%, #e0c3fc 100%);
            color: #333;
            border: none;
            padding: 12px 0;
            width: 100%;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.2s;
        }
        input[type="submit"]:hover {
            background: linear-gradient(90deg, #e0c3fc 0%, #8ec5fc 100%);
        }
    </style>
</head>

<body>
    <form action="index.php" method="get">
        <label for="username">Username:</label>
        <input type="text" name="username" id="username">

        <label for="password">Password:</label>
        <input type="password" name="password" id="password">

        <label for="gmail">Gmail:</label>
        <input type="email" name="gmail" id="gmail">

        <div class="checkbox-label">
            <input type="checkbox" name="rememberme" value="yes" id="rememberme">
            <label for="rememberme" style="font-weight:normal;">Remember me</label>
        </div>

        <label for="full_name">Full Name:</label>
        <input type="text" name="FULL_NAME" id="full_name">

        <input type="submit" value="Submit">
    </form>
</body>
</html>
<?php

echo "{$_GET["username"]} <br>";
echo "{$_GET["password"]} <br>";
echo "{$_GET["gmail"]} <br>";
echo "{$_GET["FULL_NAME"]} <br>";

?>
