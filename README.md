<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Took Long Enough Hey </title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Times               New Roman', serif; }
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #ff9acb;
            overflow: hidden;
        }
        .envelope {
            width: 350px;
            height: 250px;
            background: pink;
            border-radius: 10px;
            cursor: pointer;
            position: absolute;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        .envelope-text {
            position: absolute;
            top: 20px;
            left: 30px;
            text-align: left;
            font-size: 18px;
            font-weight: bold;
            color: rgb(255, 54, 88);
        }
        .letter {
            display: none;
            flex-direction: column;
            align-items: center;
            text-align: center;
            background: white;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .button-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        button {
            padding: 15px 25px;
            border: none;
            cursor: pointer;
            font-size: 18px;
            border-radius: 5px;
            background: rgb(255, 54, 88);
            color: white;
            transition: transform 0.3s ease;
        }
        #yes { transform-origin: center; transition: transform 0.3s ease-in-out; }
        .pulse {
            animation: pulse 0.3s ease-in-out;
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }
        .celebration {
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            position: absolute;
            width: 100%;
            text-align: center;
        }
        .heart-button1 {
            width: 80px;
            height: 80px;
            background-color: rgb(255, 48, 48);
            transform: rotate(-45deg);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 50px;
            cursor: pointer;
            position: absolute;
        }
        .heart-button1::before, .heart-button1::after {
            content: "";
            width: 80px;
            height: 80px;
            background-color: rgb(255, 48, 48);
            border-radius: 50%;
            position: absolute;
        }
        .heart-button1::before { top: -40px; left: 0; }
        .heart-button1::after { top: -50; left: 40px; }
        .heart-button2 {
            width: 50px;
            height: 50px;
            background-color: rgb(255, 54, 88);
            transform: rotate(-45deg);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 50px;
            cursor: pointer;
            position: absolute;
        }
        .heart-button2::before, .heart-button2::after {
            content: "";
            width: 50px;
            height: 50px;
            background-color: rgb(255, 54, 88);
            border-radius: 50%;
            position: absolute;
        }
        .heart-button2::before { top: -30px; left: 0; }
        .heart-button2::after { top: -40; left: 30px; bottom: 0}
        .heart-button {
            width: 120px;
            height: 120px;
            background-color: rgb(255, 54, 88);
            position: relative;
            transform: rotate(-45deg);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 20px;
            cursor: pointer;
            animation: continuous-pulse 1s infinite alternate;
        }
        .heart-button::before, .heart-button::after {
            content: "";
            width: 120px;
            height: 120px;
            background-color: rgb(255, 54, 88);
            border-radius: 50%;
            position: absolute;
        }
        .heart-button::before { top: -60px; left: 0; }
        .heart-button::after { top: 0; left: 60px; }
        .heart-text {
            position: absolute;
            padding-bottom: 35px;
            color: white;
            font-size: 22px;
            font-weight: bold;
            transform: rotate(45deg);
            z-index: 10;
        }
        @keyframes continuous-pulse {
            0% { transform: rotate(-45deg) scale(1); }
            100% { transform: rotate(-45deg) scale(1.1); }
        }
    </style>
</head>
<body>
    <div class="envelope" id="envelope">
        <div class="envelope-text">
            <p><u>To:</u> Keneilwe Zama Shai</p>
            <p><u>From:</u> Your Future Husband</p>
        </div>
        <div class="heart-button1"></div>
        <div class="heart-button2"></div>
    </div>
    <div class="letter" id="letter">
        <p style="font-size: 24px;">Will You Be My Valentine?</p>
        <div class="button-container">
            <button id="yes">Yes</button>
            <button id="no">No</button>
        </div>
    </div>
    <div class="celebration" id="celebration">
        <div class="heart-button">
            <span class="heart-text">Slayyyyy</span>
        </div>
    </div>
    <script>
        document.getElementById('envelope').addEventListener('click', function() {
            this.style.opacity = '0';
            setTimeout(() => {
                this.style.display = 'none';
                document.getElementById('letter').style.display = 'flex';
            }, 1000);
        });
        let noClicks = 0;
        const noButton = document.getElementById('no');
        const yesButton = document.getElementById('yes');
        const noMessages = ["Nope, Try Again", "Stop Joking Around", "Okay, Last Chance"];
        noButton.addEventListener('click', function() {
            if (noClicks < 3) {
                this.textContent = noMessages[noClicks];
                this.style.position = 'absolute';
                setTimeout(() => {
                    this.style.top = Math.random() * 80 + 'vh';
                    this.style.left = Math.random() * 80 + 'vw';
                }, 50);  
                yesButton.classList.add('pulse');
                setTimeout(() => yesButton.classList.remove('pulse'), 300);
            } else {
                this.style.display = 'none';
                yesButton.style.transform = 'scale(1.5)';
            }
            noClicks++;
        });
        yesButton.addEventListener('click', function() {
            document.getElementById('letter').style.display = 'none';
            let celebration = document.getElementById('celebration');
            celebration.style.display = 'flex';
        });
    </script>
</body>
</html>
