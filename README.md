<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ساعة مبهجة</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(45deg, #ff9a9e, #fad0c4, #c3e0dc, #a1c4fd);
            background-size: 400%;
            animation: colorChange 15s ease-in-out infinite;
            direction: rtl;
        }
        .container {
            text-align: center;
            background-color: rgba(255, 255, 255, 0.9);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
            max-width: 400px;
        }
        h1 {
            color: #ff6f61;
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        #clock {
            font-size: 3em;
            color: #333;
            font-weight: bold;
            margin-bottom: 20px;
        }
        button {
            background-color: #6ab04c;
            color: white;
            border: none;
            padding: 12px 25px;
            font-size: 1.2em;
            cursor: pointer;
            border-radius: 20px;
            transition: background-color 0.3s, transform 0.2s;
        }
        button:hover {
            background-color: #219653;
            transform: scale(1.1);
        }
        @keyframes colorChange {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        @media (max-width: 600px) {
            h1 {
                font-size: 2em;
            }
            #clock {
                font-size: 2em;
            }
            button {
                padding: 10px 20px;
                font-size: 1em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>ساعة مبهجة</h1>
        <div id="clock">00:00:00</div>
        <button onclick="toggleFormat()">تبديل الصيغة</button>
    </div>
    <script>
        let is24Hour = true;

        function updateClock() {
            const now = new Date();
            let hours = is24Hour ? now.getHours() : now.getHours() % 12 || 12;
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            const period = is24Hour ? '' : (now.getHours() >= 12 ? ' م' : ' ص');
            document.getElementById('clock').textContent = `${hours}:${minutes}:${seconds}${period}`;
        }

        function toggleFormat() {
            is24Hour = !is24Hour;
            updateClock();
        }

        setInterval(updateClock, 1000);
        updateClock();
    </script>
</body>
</html>
