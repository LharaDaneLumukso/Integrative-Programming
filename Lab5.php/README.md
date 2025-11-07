<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>AJAX JSON Demo</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <main>
        <h1>AJAX JSON Demo</h1>
        <form id="userForm">
            <input type="text" id="name" name="name" placeholder="Enter your name" required>
            <button type="submit">Submit</button>
        </form>

        <pre id="response" aria-live="polite"></pre>
    </main>

    <script src="js/main.js"></script>
</body>
</html>


//php

<?php
header('Content-Type: application/json');

if ($_SERVER['REQUEST_METHOD'] !== 'POST') {
    echo json_encode(['status' => 'error', 'message' => 'Invalid request method']);
    exit;
}

$raw = file_get_contents('php://input');
$data = json_decode($raw, true);

// fallback if client sent form-encoded body
if (!is_array($data)) {
    parse_str($raw, $data);
}

$name = isset($data['name']) ? trim($data['name']) : '';
$name = htmlspecialchars($name, ENT_QUOTES, 'UTF-8');

if ($name === '') {
    echo json_encode(['status' => 'error', 'message' => 'Name is required']);
    exit;
}

echo json_encode(['status' => 'success', 'message' => "Welcome, {$name}!"]);
?>



//JavaS

document.getElementById('userForm').addEventListener('submit', async function (e) {
    e.preventDefault();

    const name = document.getElementById('name').value.trim();
    const out = document.getElementById('response');

    try {
        const res = await fetch('index.php', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ name: name })
        });

        const data = await res.json();
        // show compact JSON exactly like: {"status":"success","message":"Welcome, Maria!"}
        out.textContent = JSON.stringify(data);
    } catch (err) {
        out.textContent = JSON.stringify({ status: 'error', message: 'Request failed' });
    }
});
