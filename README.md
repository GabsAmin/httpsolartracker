<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Servo Control</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 20px;
        }

        h1 {
            color: #333;
        }

        #angleInput {
            width: 80%;
            margin-bottom: 10px;
        }

        #angleValue {
            font-size: 18px;
            font-weight: bold;
            color: #009688;
        }

        button {
            padding: 10px;
            font-size: 16px;
            background-color: #009688;
            color: #fff;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background-color: #00796b;
        }
    </style>
</head>
<body>
    <h1>Servo Motor Control</h1>
    <label for="angleInput">Set Servo Angle:</label>
    <input type="range" id="angleInput" min="0" max="180" value="90" step="1">
    <br>
    <span id="angleValue">Current Angle: 90°</span>
    <br>
    <button onclick="setServoAngle()">Set Angle</button>

    <script>
        function setServoAngle() {
            var angleInput = document.getElementById('angleInput');
            var angleValue = angleInput.value;

            // Send HTTP request to Electric Imp agent
            var xhr = new XMLHttpRequest();
            xhr.open('POST', https://agent.electricimp.com/owbGe7iPDCBz, true);
            xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
            xhr.send('angle=' + angleValue);

            // Update displayed angle value
            document.getElementById('angleValue').textContent = 'Current Angle: ' + angleValue + '°';
        }
    </script>
</body>
</html>
