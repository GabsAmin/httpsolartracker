<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Servo Control</title>
</head>
<body>
    <h1>Servo Motor Control</h1>
    <label for="angleInput">Set Servo Angle:</label>
    <input type="range" id="angleInput" min="0" max="180" value="90" step="1">
    <span id="angleValue">90</span>
    <button onclick="setServoAngle()">Set Angle</button>

    <script>
        function setServoAngle() {
            var angleInput = document.getElementById('angleInput');
            var angleValue = angleInput.value;

            // Send HTTP request to Electric Imp agent
            var xhr = new XMLHttpRequest();
            xhr.open('POST', 'https://agent.electricimp.com/YOUR_UNIQUE_AGENT_ID', true);
            xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
            xhr.send('angle=' + angleValue);

            // Update displayed angle value
            document.getElementById('angleValue').textContent = angleValue;
        }
    </script>
</body>
</html>
