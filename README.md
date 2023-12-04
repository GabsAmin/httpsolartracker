
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
