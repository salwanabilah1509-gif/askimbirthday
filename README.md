<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Surprise Ulang Tahun!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #add8e6, #87ceeb); /* Gradien biru muda */
            color: #2e4a62;
            text-align: center;
            overflow: hidden;
        }
        .container {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        h1 {
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        .game {
            display: none;
            position: relative;
            width: 100%;
            height: 100vh;
            background: linear-gradient(to bottom, #add8e6, #87ceeb);
        }
        .target {
            position: absolute;
            width: 50px;
            height: 50px;
            background: url('https://via.placeholder.com/50x50/ff0000?text=Target') no-repeat center;
            background-size: cover;
            cursor: pointer;
            border-radius: 50%;
            animation: move 2s infinite alternate;
        }
        @keyframes move {
            0% { top: 20%; left: 20%; }
            100% { top: 70%; left: 80%; }
        }
        .score {
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 1.5em;
            color: #fff;
        }
        .birthday {
            display: none;
            padding: 20px;
        }
        .birthday img {
            max-width: 300px;
            border-radius: 10px;
            margin: 20px 0;
        }
        button {
            background: #4682b4;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 1.2em;
            cursor: pointer;
            border-radius: 5px;
            margin-top: 20px;
        }
        button:hover {
            background: #5a9bd4;
        }
    </style>
</head>
<body>
    <div class="container" id="intro">
        <h1>Selamat Datang di Surprise Ulang Tahun!</h1>
        <p>Untuk masuk ke surprise spesial, mainkan game tembak-tembakan dulu ya! Klik target yang muncul sebanyak 5 kali.</p>
        <button onclick="startGame()">Mulai Game</button>
    </div>

    <div class="game" id="game">
        <div class="score">Score: <span id="score">0</span>/5</div>
        <div class="target" id="target" onclick="hitTarget()"></div>
    </div>

    <div class="birthday" id="birthday">
        <h1>Happy Birthday, [Nama Pacar]! 🎉</h1>
        <p>Selamat ulang tahun, sayang! Semoga harimu penuh kebahagiaan, cinta, dan kejutan manis. Aku sayang banget sama kamu! 💖</p>
        <img src="https://via.placeholder.com/300x200/ffb6c1?text=Gambar+Surprise" alt="Gambar Surprise">
        <p>Klik di sini untuk lagu spesial: <a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ" target="_blank">Lagu Romantis</a></p>
        <button onclick="reset()">Main Lagi</button>
    </div>

    <script>
        let score = 0;
        const target = document.getElementById('target');
        const game = document.getElementById('game');
        const intro = document.getElementById('intro');
        const birthday = document.getElementById('birthday');
        const scoreDisplay = document.getElementById('score');

        function startGame() {
            intro.style.display = 'none';
            game.style.display = 'block';
            score = 0;
            scoreDisplay.textContent = score;
            moveTarget();
        }

        function moveTarget() {
            const x = Math.random() * (window.innerWidth - 50);
            const y = Math.random() * (window.innerHeight - 50);
            target.style.left = x + 'px';
            target.style.top = y + 'px';
        }

        function hitTarget() {
            score++;
            scoreDisplay.textContent = score;
            if (score >= 5) {
                game.style.display = 'none';
                birthday.style.display = 'block';
            } else {
                moveTarget();
            }
        }

        function reset() {
            birthday.style.display = 'none';
            intro.style.display = 'flex';
        }
    </script>
</body>
</html>
