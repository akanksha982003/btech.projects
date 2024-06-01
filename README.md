 Create a digital clock that displays the current time.
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initialscale=1.0">
 <title>Enhanced Digital Clock</title>
 <style>
 body {
 display: flex;
 justify-content: center;
 align-items: center;
 height: 100vh;
 background-color: #282c34;
 color: white;
 font-family: 'Arial', sans-serif;
 margin: 0;
 flex-direction: column;
 }
 .clock-container {
 display: flex;
 flex-direction: column;
 justify-content: center;
 align-items: center;
 border: 2px solid #61dafb;
 padding: 40px;
 border-radius: 10px;
 box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
 background-color: #333;
 }
 #clock {
 font-size: 96px;
 letter-spacing: 4px;
 }
 #date {
 font-size: 24px;
 margin-top: 10px;
 }
 #ampm {
 font-size: 48px;
 margin-top: 10px;
 }
 .color-picker {
 margin-top: 20px;
 }
 .color-picker label {
 margin-right: 10px;
 }
 </style>
</head>
<body>
 <div class="clock-container">
 <div id="clock"></div>
 <div id="ampm"></div>
 <div id="date"></div>
 </div>
 <div class="color-picker">
 <label for="bgColor">Background Color:</label>
 <input type="color" id="bgColor" name="bgColor"
value="#282c34">
 <label for="textColor">Text Color:</label>
 <input type="color" id="textColor" name="textColor"
value="#ffffff">
 </div>
 <script>
 function updateClock() {
 const clockElement = document.getElementById('clock');
 const ampmElement = document.getElementById('ampm');
 const dateElement = document.getElementById('date');
 const now = new Date();
 const hours = now.getHours();
 const minutes = String(now.getMinutes()).padStart(2, '0');
 const seconds = String(now.getSeconds()).padStart(2, '0');
 const ampm = hours >= 12 ? 'PM' : 'AM';
 const displayHours = String(hours % 12 || 12).padStart(2, '0');
 const day = String(now.getDate()).padStart(2, '0');
 const month = String(now.getMonth() + 1).padStart(2, '0');
 const year = now.getFullYear();
 clockElement.textContent =
`${displayHours}:${minutes}:${seconds}`;
 ampmElement.textContent = ampm;
 dateElement.textContent = `${month}/${day}/${year}`;
 }
 function setColor() {
 const bgColor = document.getElementById('bgColor').value;
 const textColor = document.getElementById('textColor').value;
 document.body.style.backgroundColor = bgColor;
 document.querySelector('.clock-container').style.color =
textColor;
 }
 document.getElementById('bgColor').addEventListener('input',
setColor);
 document.getElementById('textColor').addEventListener('input',
setColor);
 setInterval(updateClock, 1000);
 updateClock();
 setColor();
 </script>
</body>
</html>
