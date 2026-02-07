<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Swara 🌹</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Montserrat:wght@300;400;600&display=swap');

        :root {
            --bg-color: #fff0f3; /* Soft Baby Pink/Cream */
            --envelope-main: #ffb3c1;
            --envelope-flap: #ff8fa3;
            --accent: #c9184a;
        }

        body, html {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: var(--bg-color);
            font-family: 'Montserrat', sans-serif;
            overflow: hidden;
        }

        /* --- Big Heart Pop Animation --- */
        #giant-pop {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            font-size: 300px;
            color: var(--accent);
            z-index: 100;
            pointer-events: none;
            opacity: 0;
        }

        .heart-burst {
            animation: burst 1.2s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        @keyframes burst {
            0% { transform: translate(-50%, -50%) scale(0); opacity: 0; }
            50% { transform: translate(-50%, -50%) scale(1.5); opacity: 0.9; }
            100% { transform: translate(-50%, -50%) scale(3); opacity: 0; }
        }

        /* --- Envelope Setup --- */
        .scene {
            position: relative;
            text-align: center;
            z-index: 10;
        }

        .envelope {
            position: relative;
            width: 300px;
            height: 200px;
            background: var(--envelope-main);
            border-bottom-left-radius: 15px;
            border-bottom-right-radius: 15px;
            cursor: pointer;
            box-shadow: 0 15px 35px rgba(201, 24, 74, 0.2);
            transition: transform 0.3s;
        }

        .envelope:hover {
            transform: translateY(-5px);
        }

        /* The Flap */
        .flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 150px solid transparent;
            border-right: 150px solid transparent;
            border-top: 120px solid var(--envelope-flap);
            transform-origin: top;
            transition: transform 0.6s ease;
            z-index: 4;
        }

        /* The Seal */
        .seal {
            position: absolute;
            bottom: 70px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 60px;
            background: var(--accent);
            border-radius: 50%;
            z-index: 5;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 25px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            transition: 0.4s;
        }

        /* --- The Hidden Letter --- */
        .letter {
            position: absolute;
            top: 5px;
            left: 15px;
            width: 270px;
            height: 180px;
            background: white;
            z-index: 2;
            transition: 0.8s cubic-bezier(0.4, 0, 0.2, 1);
            border-radius: 10px;
            padding: 20px;
            box-sizing: border-box;
            display: flex;
            flex-direction: column;
            justify-content: center;
            opacity: 0;
            transform: translateY(0);
        }

        /* --- Open State Classes --- */
        .open .flap {
            transform: rotateX(180deg);
            z-index: 1;
        }

        .open .seal {
            opacity: 0;
            transform: translateX(-50%) scale(0);
        }

        .open .letter {
            opacity: 1;
            transform: translateY(-220px);
            height: 400px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.1);
            z-index: 6;
        }

        /* --- Aesthetic Text --- */
        .letter h1 {
            font-family: 'Dancing Script', cursive;
            color: var(--accent);
            font-size: 2.2rem;
            margin: 0 0 15px 0;
        }

        .letter p {
            font-size: 1rem;
            color: #444;
            line-height: 1.6;
            margin: 5px 0;
        }

        .highlight {
            font-weight: 600;
            color: #000;
        }

        .intro-text {
            margin-top: 30px;
            color: var(--accent);
            font-weight: 600;
            font-size: 1.2rem;
            letter-spacing: 1px;
            animation: pulse 2s infinite;
        }

        /* --- Falling Items --- */
        .falling {
            position: fixed;
            top: -50px;
            pointer-events: none;
            z-index: 50;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to { transform: translateY(110vh) rotate(360deg); }
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.7; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.05); }
        }
    </style>
</head>
<body>

    <div id="giant-pop">❤️</div>

    <div class="scene">
        <div class="envelope" id="env" onclick="handleOpen()">
            <div class="flap"></div>
            <div class="seal">❤️</div>
            <div class="letter">
                <h1>Happy Rose Day, Swara</h1>
                <p class="highlight">I wish I could give you a rose in person like before…</p>
                <p>But now all I can give is this message and the feelings I still can’t forget.</p>
            </div>
        </div>
        <div class="intro-text">For my dear Swara ❤️❤️❤️</div>
    </div>

    <script>
        function handleOpen() {
            const env = document.getElementById('env');
            const giantPop = document.getElementById('giant-pop');
            
            if (!env.classList.contains('open')) {
                // 1. Trigger the Big Heart Pop
                giantPop.classList.add('heart-burst');

                // 2. Open the Envelope after a tiny delay for impact
                setTimeout(() => {
                    env.classList.add('open');
                }, 200);

                // 3. Start falling petals and hearts
                setInterval(createFalling, 300);
            }
        }

        function createFalling() {
            const items = ['🌹', '🌸', '❤️', '💖', '✨', '🌹'];
            const el = document.createElement('div');
            el.className = 'falling';
            el.innerHTML = items[Math.floor(Math.random() * items.length)];
            el.style.left = Math.random() * 100 + 'vw';
            el.style.fontSize = Math.random() * 25 + 15 + 'px';
            el.style.animationDuration = Math.random() * 3 + 3 + 's';
            el.style.opacity = Math.random() * 0.5 + 0.5;
            
            document.body.appendChild(el);
            setTimeout(() => el.remove(), 6000);
        }
    </script>
</body>
</html>
