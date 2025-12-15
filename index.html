<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Duelo de Neón</title>
    <style>
        /* --- ESTILOS (CSS) --- */
        body {
            margin: 0;
            padding: 0;
            background-color: #121212;
            font-family: 'Arial', sans-serif;
            overflow: hidden; /* Evita scroll */
            user-select: none; /* Evita seleccionar texto al hacer clic rápido */
        }

        #game-container {
            display: flex;
            flex-direction: column;
            height: 100vh;
            width: 100%;
        }

        /* Área de puntuación y Barra central */
        #status-bar {
            height: 15%;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            background: #1a1a1a;
            border-bottom: 2px solid #333;
        }

        h1 {
            color: white;
            font-size: 1.2rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            z-index: 2;
        }

        /* La barra de "Tira y Afloja" */
        #progress-container {
            position: absolute;
            bottom: 0;
            left: 0;
            height: 10px;
            width: 100%;
            background: #333;
        }

        #progress-fill {
            height: 100%;
            width: 50%; /* Empieza al medio */
            background: linear-gradient(90deg, #ff0055 0%, #00e5ff 100%);
            transition: width 0.1s ease-out;
        }

        /* Área de juego principal */
        #play-area {
            flex: 1;
            display: flex;
            width: 100%;
        }

        /* Botones de los jugadores */
        .player-zone {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: background 0.1s;
            position: relative;
        }

        /* Jugador 1 (Rojo/Izquierda) */
        #p1-zone {
            background-color: rgba(255, 0, 85, 0.1);
            border-right: 1px solid #333;
        }
        #p1-zone:active, #p1-zone.active {
            background-color: rgba(255, 0, 85, 0.4);
            box-shadow: inset 0 0 20px #ff0055;
        }
        .p1-text { color: #ff0055; }

        /* Jugador 2 (Azul/Derecha) */
        #p2-zone {
            background-color: rgba(0, 229, 255, 0.1);
        }
        #p2-zone:active, #p2-zone.active {
            background-color: rgba(0, 229, 255, 0.4);
            box-shadow: inset 0 0 20px #00e5ff;
        }
        .p2-text { color: #00e5ff; }

        /* Textos e Instrucciones */
        .instruction {
            font-size: 1rem;
            font-weight: bold;
            text-align: center;
            margin-bottom: 10px;
        }
        .key-hint {
            font-size: 2rem;
            border: 2px solid currentColor;
            padding: 10px 20px;
            border-radius: 10px;
            opacity: 0.7;
        }

        /* Pantalla de Ganador */
        #modal {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9);
            display: none; /* Oculto por defecto */
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10;
        }
        #winner-text {
            font-size: 3rem;
            font-weight: bold;
            color: white;
            margin-bottom: 20px;
            text-shadow: 0 0 10px white;
        }
        button {
            padding: 15px 30px;
            font-size: 1.2rem;
            cursor: pointer;
            background: white;
            border: none;
            border-radius: 5px;
            font-weight: bold;
        }
        button:hover { background: #ddd; }

    </style>
</head>
<body>

    <div id="modal">
        <div id="winner-text">¡GANA JUGADOR 1!</div>
        <button onclick="resetGame()">Jugar de nuevo</button>
    </div>

    <div id="game-container">
        <div id="status-bar">
            <h1>Duelo de Neón</h1>
            <div id="progress-container">
                <div id="progress-fill"></div>
            </div>
        </div>

        <div id="play-area">
            <div id="p1-zone" class="player-zone" ontouchstart="handleInput(1)" onclick="handleInput(1)">
                <div class="instruction p1-text">JUGADOR 1</div>
                <div class="key-hint p1-text">Tecla 'A'</div>
                <div style="font-size: 0.8rem; color: #aaa; margin-top:5px;">(o toca aquí)</div>
            </div>

            <div id="p2-zone" class="player-zone" ontouchstart="handleInput(2)" onclick="handleInput(2)">
                <div class="instruction p2-text">JUGADOR 2</div>
                <div class="key-hint p2-text">Tecla 'L'</div>
                <div style="font-size: 0.8rem; color: #aaa; margin-top:5px;">(o toca aquí)</div>
            </div>
        </div>
    </div>

    <script>
        /* --- LÓGICA DEL JUEGO (JS) --- */
        
        // Estado del juego
        let score = 50; // 0 = Gana P1, 100 = Gana P2. Empieza en 50.
        let gameActive = true;
        
        // Configuración de dificultad (cuánto empuja cada clic)
        const PUSH_POWER = 3; 

        // Referencias al DOM
        const fill = document.getElementById('progress-fill');
        const modal = document.getElementById('modal');
        const winnerText = document.getElementById('winner-text');
        const p1Zone = document.getElementById('p1-zone');
        const p2Zone = document.getElementById('p2-zone');

        // Escuchar teclado
        document.addEventListener('keydown', (e) => {
            if (!gameActive) return;

            // Jugador 1 usa la tecla 'A' o 'a'
            if (e.key === 'a' || e.key === 'A') {
                handleInput(1);
                highlightZone(p1Zone);
            }
            // Jugador 2 usa la tecla 'L' o 'l'
            else if (e.key === 'l' || e.key === 'L') {
                handleInput(2);
                highlightZone(p2Zone);
            }
        });

        // Función principal de movimiento
        function handleInput(player) {
            if (!gameActive) return;

            if (player === 1) {
                score -= PUSH_POWER; // Mueve la barra a la izquierda
            } else {
                score += PUSH_POWER; // Mueve la barra a la derecha
            }

            updateDisplay();
            checkWin();
        }

        // Efecto visual al presionar tecla
        function highlightZone(element) {
            element.classList.add('active');
            setTimeout(() => element.classList.remove('active'), 100);
        }

        // Actualizar la barra gráfica
        function updateDisplay() {
            // Limitar score visualmente entre 0 y 100
            let displayScore = Math.max(0, Math.min(100, score));
            fill.style.width = displayScore + '%';
        }

        // Comprobar si alguien ganó
        function checkWin() {
            if (score <= 0) {
                endGame("¡GANA JUGADOR 1!", "#ff0055");
            } else if (score >= 100) {
                endGame("¡GANA JUGADOR 2!", "#00e5ff");
            }
        }

        // Terminar juego
        function endGame(text, color) {
            gameActive = false;
            winnerText.innerText = text;
            winnerText.style.color = color;
            winnerText.style.textShadow = `0 0 20px ${color}`;
            modal.style.display = 'flex';
        }

        // Reiniciar juego
        function resetGame() {
            score = 50;
            gameActive = true;
            updateDisplay();
            modal.style.display = 'none';
        }
    </script>
</body>
</html>
