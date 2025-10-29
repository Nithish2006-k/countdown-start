<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Count-Up Timer</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #1e1e2f;
      color: rgb(236, 234, 234);
      text-align: center;
      padding: 50px;
    }
    h1 {
      font-size: 2.5em;
      margin-bottom: 20px;
    }
    .timer {
      display: flex;
      justify-content: center;
      gap: 30px;
      font-size: 2em;
      margin-bottom: 30px;
    }
    .timer div {
      background: rgba(255, 255, 255, 0.1);
      padding: 20px;
      border-radius: 10px;
      min-width: 100px;
    }
    .label {
      font-size: 0.5em;
      margin-top: 10px;
      display: block;
    }
    button {
      margin: 10px;
      padding: 10px 20px;
      font-size: 1em;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    #startBtn {
      background-color: #0f1110;
      color: white;
    }
    #stopBtn {
      background-color: #111010;
      color: white;
    }
    #resetBtn {
      background-color: #0e0d0d;
      color: rgb(247, 239, 239);
    }
  </style>
</head>
<body>
  <h1>Count-Up Timer</h1>
  <div class="timer">
    <div><span id="days">00</span><span class="label">Days</span></div>
    <div><span id="hours">00</span><span class="label">Hours</span></div>
    <div><span id="minutes">00</span><span class="label">Minutes</span></div>
    <div><span id="seconds">00</span><span class="label">Seconds</span></div>
  </div>
  <button id="startBtn">Start</button>
  <button id="stopBtn">Stop</button>
  <button id="resetBtn">Reset</button>

  <script>
    let interval;
    let elapsed = 0;
    let isRunning = false;

    function updateTimer() {
      elapsed += 1;
      const days = Math.floor(elapsed / (60 * 60 * 24));
      const hours = Math.floor((elapsed % (60 * 60 * 24)) / (60 * 60));
      const minutes = Math.floor((elapsed % (60 * 60)) / 60);
      const seconds = elapsed % 60;

      document.getElementById("days").textContent = String(days).padStart(2, '0');
      document.getElementById("hours").textContent = String(hours).padStart(2, '0');
      document.getElementById("minutes").textContent = String(minutes).padStart(2, '0');
      document.getElementById("seconds").textContent = String(seconds).padStart(2, '0');
    }

    document.getElementById("startBtn").addEventListener("click", () => {
      if (!isRunning) {
        interval = setInterval(updateTimer, 1000);
        isRunning = true;
      }
    });

    document.getElementById("stopBtn").addEventListener("click", () => {
      clearInterval(interval);
      isRunning = false;
    });

    document.getElementById("resetBtn").addEventListener("click", () => {
      clearInterval(interval);
      isRunning = false;
      elapsed = 0;
      document.getElementById("days").textContent = "00";
      document.getElementById("hours").textContent = "00";
      document.getElementById("minutes").textContent = "00";
      document.getElementById("seconds").textContent = "00";
    });
  </script>
</body>
</html>
