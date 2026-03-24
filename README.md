<?php
session_start();
error_reporting(0);
require 'config.php';

// OAuth URL
$auth_url = "https://github.com/login/oauth/authorize?client_id=".CLIENT_ID."&scope=repo,user,delete_repo";
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitFlow — Access</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
    <style>
        :root { --bg: #000; --fg: #fff; --accents: #111; --border: #333; }
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background: var(--bg); color: var(--fg); display: flex; align-items: center; justify-content: center; height: 100vh; overflow: hidden; }
        .ambient { position: absolute; top: 0; width: 100%; height: 400px; background: radial-gradient(circle at top, rgba(255,255,255,0.05) 0%, transparent 70%); z-index: 0; }
        .card { width: 100%; max-width: 380px; padding: 20px; z-index: 10; text-align: center; }
        .logo { width: 45px; margin-bottom: 25px; filter: drop-shadow(0 0 10px rgba(255,255,255,0.2)); }
        h1 { font-size: 1.8rem; font-weight: 800; letter-spacing: -1px; margin-bottom: 30px; }
        input { width: 100%; background: var(--accents); border: 1px solid var(--border); padding: 15px; border-radius: 8px; color: #fff; margin-bottom: 15px; outline: none; }
        input:focus { border-color: #666; }
        .btn { width: 100%; padding: 15px; border-radius: 8px; font-weight: 600; cursor: pointer; border: none; transition: 0.2s; text-decoration: none; display: flex; align-items: center; justify-content: center; gap: 10px; font-size: 0.9rem; }
        .btn-primary { background: #fff; color: #000; }
        .btn-secondary { background: transparent; color: #fff; border: 1px solid var(--border); margin-top: 10px; }
        .btn:hover { opacity: 0.8; }
        .divider { margin: 25px 0; display: flex; align-items: center; color: #444; font-size: 0.7rem; letter-spacing: 1px; }
        .divider::before, .divider::after { content: ""; flex: 1; height: 1px; background: #222; margin: 0 10px; }
        .footer { margin-top: 25px; font-size: 0.8rem; color: #555; }
        .footer a { color: #0070f3; text-decoration: none; }
    </style>
</head>
<body>
    <div class="ambient"></div>
    <div class="card">
        <svg class="logo" viewBox="0 0 75 65" fill="none"><path d="M37.5 0L75 65H0L37.5 0Z" fill="white"/></svg>
        <h1>Login to GitFlow</h1>
        
        <form action="dashboard.php" method="POST">
            <input type="text" name="access_token" placeholder="Paste Personal Access Token" required>
            <button type="submit" class="btn btn-primary">Continue with Token</button>
        </form>

        <div class="divider">OR</div>

        <a href="<?= $auth_url ?>" class="btn btn-secondary">
            <i class="fab fa-github"></i> Continue with GitHub
        </a>

        <div class="footer">
            Don't have a token? <a href="https://github.com/settings/tokens" target="_blank">Get it here</a>
        </div>
    </div>
</body>
</html>
