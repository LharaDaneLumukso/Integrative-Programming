<?php

$jsonString = '{"name":"Maria","age":21,"email":"maria@example.com"}';


$objectData = json_decode($jsonString);


$arrayData = json_decode($jsonString, true);


echo "Object: " . $objectData->name . "<br>";
echo "Array: " . $arrayData["email"] . "<br>";
?>
