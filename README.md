<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <title>Professional Manual Scoreboard</title>
    <style>
        body { background-color: transparent; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; padding: 20px; overflow: hidden; }
        
        .scoreboard {
            display: flex;
            align-items: center;
            background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            color: white;
            width: fit-content;
            padding: 10px 25px;
            border-radius: 50px;
            border: 2px solid #f1c40f;
            box-shadow: 0 5px 15px rgba(0,0,0,0.5);
        }

        .live-indicator {
            width: 12px; height: 12px; background: #ff0000;
            border-radius: 50%; margin-right: 15px;
            animation: blink 1.2s infinite;
        }

        .team { font-weight: 800; font-size: 22px; color: #fff; text-transform: uppercase; margin-right: 15px; }
        .score { font-size: 30px; color: #f1c40f; font-weight: bold; margin-right: 10px; }
        .overs { font-size: 18px; color: #bdc3c7; }

        @keyframes blink { 50% { opacity: 0.3; } }
    </style>
</head>
<body>

    <div class="scoreboard">
        <div class="live-indicator"></div>
        <div class="team" id="teamName">TEAM</div>
        <div class="score" id="liveScore">0/0</div>
        <div class="overs" id="liveOvers">(0.0)</div>
    </div>

    <script>
        // ইউআরএল থেকে ডেটা পড়ার ফাংশন
        function updateFromURL() {
            const params = new URLSearchParams(window.location.search);
            
            if(params.has('team')) document.getElementById('teamName').innerText = params.get('team');
            if(params.has('score')) document.getElementById('liveScore').innerText = params.get('score');
            if(params.has('overs')) document.getElementById('liveOvers').innerText = "(" + params.get('overs') + ")";
        }

        // প্রতি ১ সেকেন্ড পরপর চেক করবে লিঙ্ক পরিবর্তন হয়েছে কি না
        setInterval(updateFromURL, 1000);
        window.onload = updateFromURL;
    </script>
</body>
</html>
