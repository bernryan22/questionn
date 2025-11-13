<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Busy ka ba?</title>
    <style>
        body {
            font-family: Dancing Script, sans-serif;
            text-align: center;
            margin-top: 100px;
        }
        #question {
            font-size: 24px;
            margin-bottom: 20px;
        }
        button {
            font-size: 18px;
            padding: 10px 20px;
            margin: 10px;
            cursor: pointer;
        }
        #no {
            position: relative;
        }
        #message {
            display: none;
            font-size: 24px;
            color: green;
            margin-top: 20px;
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

        // Move No button on hover
        noBtn.addEventListener('mouseover', () => {
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 100);
            noBtn.style.left = `${x}px`;
            noBtn.style.top = `${y}px`;
            noBtn.style.position = 'absolute';
        });

        // On Yes click, show message
        yesBtn.addEventListener('click', () => {
            question.style.display = 'none';
            yesBtn.style.display = 'none';
            noBtn.style.display = 'none';
            message.style.display = 'block';
        });

        // On No click, reset (infinite loop)
        noBtn.addEventListener('click', () => {
            // Reset position and visibility
            noBtn.style.position = 'static';
            question.style.display = 'block';
            yesBtn.style.display = 'inline-block';
            noBtn.style.display = 'inline-block';
            message.style.display = 'none';
        });
    </script>
</body>
</html>
