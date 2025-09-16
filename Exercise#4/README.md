<?php
file_put_contents('data.txt', print_r($_POST, true));
$team = [
    [
        'name' => 'Leila C. Lozada',
        'age' => '21',
        'gender' => 'Female',
        'location' => 'Bacoor Cavite City',
        'img' => 'images/527591977_4285321085066962_2079778916863737326_n.jpg',
        'desc' => 'Every line of code is a decision that shapes the future.'
    ],
    [
        'name' => 'Joanna Mae S. Hachaso',
        'age' => '20',
        'gender' => 'Female',
        'location' => 'Poblacion Muntinlupa City',
        'img' => 'images/527719458_3286305481535647_230781896056068238_n.jpg',
        'desc' => 'Learning to program is like training my brain to think in algorithms each breakthrough fuels my curiosity even more.'
    ],
    [
        'name' => 'Lhara Dane Lumukso',
        'age' => '20',
        'gender' => 'Female',
        'location' => 'Poblacion Muntinlupa City',
        'img' => 'images/527506655_1246869533417378_9120113770127879063_n.jpg',
        'desc' => "The deeper I dive into programming, the more I realize it's not just about syntax—it's about shaping ideas into reality."
    ],
    [
        'name' => 'John Robert A. Viernes',
        'age' => '22',
        'gender' => 'Male',
        'location' => 'Katarungan Village 1, Poblacion Muntinlupa City',
        'img' => 'images/c773eb4b-6ec0-4083-af33-e08840333eb0.jpg',
        'desc' => "Programming isn't just a skill—it's a puzzle that keeps evolving, and I love chasing the thrill of solving it."
    ]
];

$error = '';
// Default values for form fields
$name = $team[2]['name'];
$age = $team[2]['age'];
$gender = $team[2]['gender'];
$address = $team[2]['location'];

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $name = trim($_POST['name']);
    $age = trim($_POST['age']);
    $gender = trim($_POST['gender']);
    $address = trim($_POST['address']);
    if ($name === '' || $age === '' || !is_numeric($age) || $age < 1 || $age > 120 || $gender === '' || $address === '') {
        $error = 'Please enter valid values for all fields.';
    } else {
        $team[2]['name'] = $name;
        $team[2]['age'] = $age;
        $team[2]['gender'] = $gender;
        $team[2]['location'] = $address;
    }
}
?>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>EXERCISE 1 HTML WITH CSS</title>
  <link rel="icon" type="image/png" href="images/favicon.png">
  <style>
    body {
      font-family: Arial;
      background-color: #521b21; 
      align-items: center;
      color: #9b6666fb;
      margin: 0;
    }
    .TEAMPROFILE {
      text-align: center;
      padding: 50px 20px;
    }
    form {
      background: #fff6fa;
      border: 2px solid #ffb6d5;
      border-radius: 12px;
      padding: 20px;
      display: inline-block;
      margin-bottom: 30px;
      box-sizing: border-box;
      max-width: 100%;
    }
    form label {
      margin-right: 15px;
      font-weight: 600;
      color: #521b21;
      display: inline-block;
    }
    form input[type="text"],
    form input[type="number"] {
      border: 1px solid #ffb6d5;
      margin-right: 10px;
      margin-bottom: 10px;
      width: 120px;
      box-sizing: border-box;
    }
    form button {
      background: #ff007f;
      color: #fff;
      border: none;
      border-radius: 6px;
      padding: 8px 18px;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.2s;
    }
    form button:hover {
      background: #9e6680;
    }
    .error-message {
      color: #d8000c;
      background: #ffd2d2;
      border: 1px solid #d8000c;
      border-radius: 6px;
      padding: 8px;
      margin-bottom: 10px;
      display: inline-block;
    }
    .J h1 {
      font-size: 48px;
      font-weight: bold;
      margin-bottom: 40px;
    }
    .J h1 span {
      color: #9e6680;
    }
    .R {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 30px;
    }
    .team-member {
      background-color: #fff6fa; 
      color: #222;
      width: 220px;
      padding: 20px;
      border-radius: 16px;
      text-align: center;
      border: 2px solid #ffb6d5; 
      position: relative;
      transition: transform 0.2s, box-shadow 0.2s;
      box-sizing: border-box;
    }
    .team-member:hover {
      transform: translateY(-20px);
      box-shadow: 0 8px 24px rgba(158, 102, 128, 0.2);
    }
    .team-member img {
      width: 120px;
      height: 130px;
      border-radius: 50%;
      object-fit: cover;
      display: block;
      margin: 0 auto 12px auto;
      border: 3px solid #ffb6d5;
      background: #fff;
    }
    .team-member h2 {
      font-size: 20px;
      font-weight: 700;
      margin: 10px 0 8px;
      color: #ff007f;
      font-family: 'Segoe UI', Arial, sans-serif;
      letter-spacing: 0.5px;
    }
    .team-member p {
      font-size: 15px;
      line-height: 1.2; 
      color: #444;
      margin-bottom: 2px; 
      font-family: 'Segoe 
