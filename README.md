<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Busy ka ba?</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script> <!-- Confetti library -->
    <style>
        body {
            font-family: 'Dancing Script', cursive; 
            text-align: center;
            margin-top: 100px;
            background-color: #FFB6C1; 
            background-image: linear-gradient(to bottom, #FFB6C1, #FFC0CB); 
            color: #8B0000; 
        }
        #question {
            font-size: 36px; 
            font-weight: bold;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3); 
        }
        button {
            font-size: 20px; 
            padding: 15px 30px; 
            margin: 15px;
            cursor: pointer;
            border: 3px solid #FF69B4; 
            border-radius: 10px; 
            background-color: #FFF0F5; 
            color: #8B0000; 
            font-family: 'Dancing Script', cursive; 
            transition: all 0.3s ease; 
        }
        button:hover {
            background-color: #FF69B4; 
            color: white;
        }
        #no {
            position: relative;
        }
        #message {
            display: none;
            font-size: 32px;
            color: #DC143C; 
            margin-top: 20px;
            border: 4px solid #FF1493; 
            border-radius: 15px;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8); 
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }
    </style>
</head>
<body>
    <div id="question">Busy ka ba?</div>
    <button id="yes">Yes</button>
    <button id="no">No</button>
    <div id="message">penge kiss bi!</div>

    <script>
        const yesBtn = document.getElementById('yes');
        const noBtn = document.getElementById('no');
        const question = document.getElementById('question');
        const message = document.getElementById('message');

        // Function to move the No button randomly
        function moveNoButton() {
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 100);
            noBtn.style.left = `${x}px`;
            noBtn.style.top = `${y}px`;
            noBtn.style.position = 'absolute';
        }

        // Move No button on hover (desktop)
        noBtn.addEventListener('mouseover', moveNoButton);

        // Move No button on touch start (mobile) - this fixes the "stuck" issue on iOS/Android
        noBtn.addEventListener('touchstart', (e) => {
            e.preventDefault(); // Prevent default touch behavior to avoid accidental clicks
            moveNoButton();
        });

        // On Yes click, show message and trigger confetti
        yesBtn.addEventListener('click', () => {
            question.style.display = 'none';
            yesBtn.style.display = 'none';
            noBtn.style.display = 'none';
            message.style.display = 'block';
            // Trigger confetti burst
            confetti({
                particleCount: 100,
                spread: 70,
                origin: { y: 0.6 }
            });
        });

        // On No click, reset (infinite loop)
        noBtn.addEventListener('click', () => {
            // Reset position and visibility
            noBtn.style.position = 'static';
            noBtn.style.left = '';
            noBtn.style.top = '';
            question.style.display = 'block';
            yesBtn.style.display = 'inline-block';
            noBtn.style.display = 'inline-block';
            message.style.display = 'none';
        });
    </script>
</body>
</html>
