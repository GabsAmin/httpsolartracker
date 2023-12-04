<!-- HTML code for the web interface -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Servo Control</title>
</head>
<body>
    <h1>Servo Control</h1>
    <button onclick="sendCommand(0)">Move to 0 degrees</button>
    <button onclick="sendCommand(90)">Move to 90 degrees</button>
    <button onclick="sendCommand(180)">Move to 180 degrees</button>

    <script>
        function sendCommand(angle) {
            fetch('https://gabsamin.github.io/httpsolartracker/' + angle)
                .then(response => {
                    if (response.ok) {
                        console.log('Command sent successfully');
                    } else {
                        console.error('Failed to send command');
                    }
                })
                .catch(error => {
                    console.error('Error:', error);
                });
        }
    </script>
</body>
</html>
