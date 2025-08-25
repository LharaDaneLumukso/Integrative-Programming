<?php
// 1. Simple if statement (Check light status)
$lightSensor = 85;
if ($lightSensor > 70) {
    echo "Bright environment - Dimming lights\n";
}

// 2. if...else statement (User subscription check)
$isSubscribed = true;
if ($isSubscribed) {
    echo "Welcome Premium User! Access to exclusive content granted.\n";
} else {
    echo "Free User: Upgrade to premium for full access.\n";
}

// 3. if...elseif...else statement (BMI Category)
$bmi = 22.5;
if ($bmi < 18.5) {
    echo "Underweight - Consider nutritional consultation\n";
} elseif ($bmi >= 18.5 && $bmi <= 24.9) {
    echo "Healthy Weight - Keep up the good work!\n";
} elseif ($bmi >= 25 && $bmi <= 29.9) {
    echo "Overweight - Recommended to increase physical activity\n";
} else {
    echo "Obesity - Please consult a healthcare provider\n";
}

// 4. switch statement (HTTP Method Handler)
$httpMethod = "POST";
switch ($httpMethod) {
    case "GET":
        echo "Fetching resource from server\n";
        break;
    case "POST":
        echo "Creating new resource\n";
        break;
    case "PUT":
        echo "Updating existing resource\n";
        break;
    case "DELETE":
        echo "Removing resource\n";
        break;
    default:
        echo "Unsupported HTTP method\n";
}
?>
