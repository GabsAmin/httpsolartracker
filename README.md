<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Motor Control</title>
    <meta http-equiv="Permissions-Policy" content="accelerometer=(), camera=(), geolocation=(); encrypted-media=()">
    <style>
        /* Your CSS styles go here */
    </style>
</head>
<body>
    <h1>Motor Control</h1>
    <label for="speedInput">Set Motor Speed:</label>
    <input type="range" id="speedInput" min="0" max="100" value="50" step="1">
    <br>
    <span id="speedValue">Current Speed: 50%</span>
    <br>
    <button onclick="setMotorSpeed()">Set Speed</button>

    <script>
        function setMotorSpeed() {
            var speedInput = document.getElementById('speedInput');
            var speedValue = speedInput.value;

            // Send HTTP request to Electric Imp agent
            var xhr = new XMLHttpRequest();
            xhr.open('POST', 'https://agent.electricimp.com/YOUR_UNIQUE_AGENT_ID', true);
            xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
            xhr.send('speed=' + speedValue);

            // Update displayed speed value
            document.getElementById('speedValue').textContent = 'Current Speed: ' + speedValue + '%';
        }
    </script>
</body>
</html>
