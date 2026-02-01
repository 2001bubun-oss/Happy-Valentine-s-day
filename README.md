# Happy-Valentine-s-day
<!DOCTYPE html>
<html lang="en">
<head>
    <title>My Forever Valentine 💖</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            height: 100vh; overflow: hidden;
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientShift 8s ease infinite;
            font-family: 'Georgia', serif;
            cursor: none;
        }
        @keyframes gradientShift {
            0%,100% {background-position:0% 50%}
            50% {background-position:100% 50%}
        }
        .container {
            position: absolute; top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            text-align: center; color: white;
            z-index: 1000;
        }
        h1 {
            font-size: 3.5em; margin-bottom: 30px;
            background: linear-gradient(45deg, #ff6b9d, #feca57, #48dbfb, #ff9ff3);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            background-size: 300% 300%; animation: textGlow 3s ease infinite;
            text-shadow: 0 0 30px rgba(255,255,255,0.8);
            filter: drop-shadow(0 0 20px rgba(255,107,157,0.8));
        }
        @keyframes textGlow { 0%,100%{background-position:0% 50%} 50%{background-position:100% 50%} }
        
        #message { font-size: 1.4em; line-height: 1.8; max-width: 700px; margin: 0 auto 40px;
            text-shadow: 2px 2px 10px rgba(0,0,0,0.7); opacity: 0; animation: fadeInUp 2s 1s forwards; }
        @keyframes fadeInUp { to { opacity: 1; transform: translateY(0); } }
        
        .glow-btn {
            background: linear-gradient(45deg, #ff6b9d, #feca57);
            border: none; padding: 20px 50px; font-size: 1.8em; border-radius: 50px;
            color: white; cursor: pointer; position: relative; overflow: hidden;
            box-shadow: 0 10px 30px rgba(255,107,157,0.6), inset 0 2px 0 rgba(255,255,255,0.3);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-transform: uppercase; letter-spacing: 2px; font-weight: bold;
        }
        .glow-btn:hover {
            transform: translateY(-5px) scale(1.05); box-shadow: 0 20px 40px rgba(255,107,157,0.8);
        }
        .glow-btn:active { transform: scale(0.95); }
        
        /* 3D Floating Hearts */
        .heart-float {
            position: absolute; color: #ff6b9d; font-size: 20px;
            animation: float 6s infinite linear; pointer-events: none;
        }
        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg) scale(0); opacity: 1; }
            50% { opacity: 1; transform: translateY(50vh) rotate(180deg) scale(1.2); }
            100% { transform: translateY(-100px) rotate(360deg) scale(0); opacity: 0; }
        }
        
        /* Fireworks */
        .firework {
            position: absolute; width: 4px; height: 4px; background: #fff;
            border-radius: 50%; pointer-events: none;
        }
        .firework::before { content: ''; position: absolute; width: 100%; height: 100%;
            background: inherit; border-radius: inherit; animation: explode 1s forwards; }
        
        /* Custom Cursor */
        body::after {
            content: '💖'; position: fixed; pointer-events: none; z-index: 9999;
            font-size: 25px; transform: translate(-50%, -50%);
            animation: cursorFloat 2s infinite ease-in-out;
        }
        @keyframes cursorFloat { 0%,100%{transform:translate(-50%,-50%) scale(1) rotate(0deg)}
        50%{transform:translate(-50%,-50%) scale(1.2) rotate(180deg)}}
    </style>
</head>
<body>
    <div class="container">
        <h1>Will You Be My Valentine? 💕</h1>
        <div id="message"></div>
        <button class="glow-btn" onclick="acceptLove()">YES! Forever! ✨</button>
    </div>

    <script>
        // Romantic Messages
        const messages = [
            "From the moment I met you, my heart knew you were the one.",
            "Every moment with you feels like a beautiful dream.",
            "You make my world brighter, my days sweeter, my life complete.",
            "I want to hold your hand, dance in the rain, grow old together.",
            "Be my Valentine today... tomorrow... and always? 💖"
        ];
        
        // Typewriter Effect
        let msgIndex = 0, charIndex = 0;
        function typeMessage() {
            if (charIndex < messages[msgIndex].length) {
                document.getElementById('message').innerHTML += messages[msgIndex].charAt(charIndex);
                charIndex++;
                setTimeout(typeMessage, 80);
            } else {
                setTimeout(() => {
                    charIndex = 0; document.getElementById('message').innerHTML = '';
                    msgIndex = (msgIndex + 1) % messages.length;
                    typeMessage();
                }, 3000);
            }
        }
        typeMessage();
        
        // 3D Floating Hearts
        setInterval(() => {
            const heart = document.createElement('div');
            heart.className = 'heart-float';
            heart.innerHTML = ['💖','💕','💗','💝','🌹'][Math.floor(Math.random()*5)];
            heart.style.left = Math.random() * 100 + '%';
            heart.style.animationDuration = (Math.random()*3 + 4) + 's';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 8000);
        }, 400);
        
        // Fireworks on Click
        document.addEventListener('click', explode);
        function explode(e) {
            for(let i = 0; i < 15; i++) {
                const firework = document.createElement('div');
                firework.className = 'firework';
                const angle = (i / 15) * Math.PI * 2;
                const velocity = 100 + Math.random() * 100;
                firework.style.left = e.clientX + 'px';
                firework.style.top = e.clientY + 'px';
                firework.style.background = `hsl(${Math.random()*360}, 100%, 70%)`;
                document.body.appendChild(firework);
                setTimeout(() => firework.remove(), 1000);
            }
        }
        
        // Victory Celebration
        function acceptLove() {
            document.querySelector('.glow-btn').style.display = 'none';
            document.getElementById('message').innerHTML = 
                '🎉 I LOVE YOU! You made me the happiest person alive! 💖✨<br>' +
                'Forever starts NOW! 💕💍🌹';
            
            // Victory Fireworks + Confetti
            for(let i = 0; i < 100; i++) setTimeout(() => explode({clientX: Math.random()*window.innerWidth, clientY: Math.random()*window.innerHeight}), i*50);
        }
        
        // Mobile Touch Support
        document.addEventListener('touchstart', e => explode({clientX: e.touches[0].clientX, clientY: e.touches[0].clientY}));
    </script>
</body>
</html>
