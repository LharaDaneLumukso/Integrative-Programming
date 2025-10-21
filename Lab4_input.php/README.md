<?php
file_put_contents("data.txt",  print_r($_POST, true)); 
?>
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Input Form</title>
        <style>
            
            :root{
                --bg:#f4f7fb;
                --card:#ffffff;
                --accent:#2b6cb0;
                --muted:#6b6f76;
            }
            html,body{
                height:100%;
                margin:0;
                font-family:system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
                background:linear-gradient(180deg, var(--bg), #eef3f8);
                color:#111827;
            }
            .wrap{
                min-height:100%;
                display:flex;
                align-items:center;
                justify-content:center;
                padding:40px 16px;
            }
            .card{
                background:var(--card);
                width:100%;
                max-width:420px;
                padding:24px;
                border-radius:12px;
                box-shadow:0 6px 18px rgba(23,31,49,0.08);
                border:1px solid rgba(15,23,42,0.03);
            }
            h1{
                margin:0 0 12px 0;
                font-size:20px;
                font-weight:600;
                color:#0f172a;
            }
            .field{
                display:flex;
                flex-direction:column;
                gap:6px;
                margin-bottom:14px;
            }
            label{
                font-size:13px;
                color:var(--muted);
            }
            input[type="text"]{
                padding:10px 12px;
                font-size:15px;
                border:1px solid #d6d9df;
                border-radius:8px;
                outline:none;
                transition:box-shadow .12s, border-color .12s;
            }
            input[type="text"]:focus{
                border-color: var(--accent);
                box-shadow:0 4px 14px rgba(43,108,176,0.12);
            }
            .btn{
                display:inline-block;
                width:100%;
                padding:10px 12px;
                background:var(--accent);
                color:#fff;
                border:none;
                border-radius:8px;
                font-size:15px;
                cursor:pointer;
            }
            .muted-note{
                margin-top:10px;
                font-size:13px;
                color:var(--muted);
                text-align:center;
            }
        </style>
    </head>
    <body>
        <div class="wrap">
            <form class="card" action="index.php" method="post">
                <h1>Input Form</h1>
                <div class="field">
                    <label for="username">Username</label>
                    <input id="username" type="text" name="Username" autocomplete="username">
                </div>
                <div class="field">
                    <label for="password">Password</label>
                    <input id="password" type="text" name="Password" autocomplete="current-password">
                </div>
                <button class="btn" type="submit">Submit</button>
                <div class="muted-note">Submitted data is saved to data.txt</div>
            </form>
        </div>
    </body>
</html>
