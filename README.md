<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bob - The Smart Robot</title>
    <style>
        body {
            font-family: 'Helvetica', sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
            color: #333;
        }

        header {
            background-color: #2a9d8f;
            color: white;
            padding: 30px;
            text-align: center;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        h1 {
            font-size: 42px;
            margin: 0;
        }

        p {
            font-size: 18px;
            margin-top: 10px;
            color: #f1f1f1;
        }

        .container {
            padding: 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        .status-box {
            background-color: #ffffff;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            flex: 1;
            margin-right: 20px;
            margin-bottom: 20px;
            text-align: center;
            transition: all 0.3s;
        }

        .status-box:hover {
            transform: translateY(-5px);
        }

        .status-box h3 {
            font-size: 24px;
            margin: 10px 0;
            color: #2a9d8f;
        }

        .status-box p {
            font-size: 18px;
            color: #777;
        }

        .action-btn {
            background-color: #2a9d8f;
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 8px;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .action-btn:hover {
            background-color: #21867a;
            transform: translateY(-3px);
        }

        .footer {
            text-align: center;
            padding: 20px;
            background-color: #2a9d8f;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

        .project-credit {
            position: fixed;
            bottom: 15px;
            right: 20px;
            font-size: 16px;
            font-weight: bold;
            color: #333;
        }

        .project-credit span {
            font-weight: normal;
            color: #2a9d8f;
        }
    </style>
</head>
<body>

<header>
    <h1>Bob - The Smart Robot</h1>
    <p>Your friendly autonomous math solver</p>
</header>

<div class="container">
    <div class="status-box">
        <h3>Robot Status</h3>
        <p id="statusText">Idle</p>
    </div>
    <div class="status-box">
        <h3>Math Solver Mode</h3>
        <p id="modeText">Inactive</p>
    </div>
</div>

<div class="container">
    <button class="action-btn" id="startBotBtn">Start Bob</button>
    <button class="action-btn" id="mathModeBtn">Math Solver Mode</button>
</div>

<div class="footer">
    <!-- Footer content -->
</div>

<!-- Project Credit -->
<div class="project-credit">
    A project powered by <span>Rejitha Mam</span>
</div>

<script>
    // Simulate starting the robot and activating math mode
    document.getElementById("startBotBtn").addEventListener("click", function() {
        document.getElementById("statusText").innerText = "Bob is Moving!";
        document.getElementById("modeText").innerText = "Inactive";
    });

    document.getElementById("mathModeBtn").addEventListener("click", function() {
        document.getElementById("statusText").innerText = "Bob is Stopped!";
        document.getElementById("modeText").innerText = "Activated";
        alert("Math Solver Mode Activated. Ask Bob a question!");
    });

    // Web Speech API for voice recognition
    const recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
    recognition.lang = 'en-US';

    recognition.onstart = function() {
        console.log("Listening for 'Hey Bob'...");
    }

    recognition.onresult = function(event) {
        const speech = event.results[0][0].transcript;
        console.log("Heard:", speech);

        if (speech.toLowerCase() === "hey bob") {
            document.getElementById("statusText").innerText = "Bob is Listening!";
            document.getElementById("modeText").innerText = "Activated";
            alert("Math Solver Mode Activated. Ask Bob a question!");
        } else {
            console.log("Unrecognized command:", speech);
        }
    }

    recognition.start();
</script>

</body>
</html>
