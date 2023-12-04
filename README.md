<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Servo Control</title>
    <!-- Include your JavaScript file here -->
    <script src="path/to/your/script.js"></script>
</head>
<body>
    <h1>Servo Motor Control</h1>
    <label for="angleInput">Set Servo Angle:</label>
    <input type="range" id="angleInput" min="0" max="180" value="90" step="1">
    <br>
    <span id="angleValue">Current Angle: 90°</span>
    <br>
    <!-- Button with the correct onclick attribute -->
    <button onclick="setServoAngle()">Set Angle</button>
</body>
</html>


// Function to set servo angle
function setServoAngle() {
    var angleInput = document.getElementById('angleInput');
    var angleValue = angleInput.value;

    // Send HTTP request to Electric Imp agent
    var xhr = new XMLHttpRequest();
    xhr.open('POST', 'https://agent.electricimp.com/YOUR_UNIQUE_AGENT_ID', true);
    xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
    xhr.send('angle=' + angleValue);

    // Update displayed angle value
    document.getElementById('angleValue').textContent = 'Current Angle: ' + angleValue + '°';
}
