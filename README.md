<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Enciclopedia de Lenguajes de Programación</title>
    <style>
        /* Todos los estilos CSS anteriores permanecen iguales */
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #2ecc71;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: var(--dark);
            line-height: 1.6;
            position: relative;
            min-height: 100vh;
        }
        
        /* Fondo animado con colores pasteles que cambian */
        .animated-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            background: linear-gradient(-45deg, #ffc8dd, #bde0fe, #a2d2ff, #cdb4db, #ffafcc, #a2d2ff, #bde0fe);
            background-size: 400% 400%;
            animation: gradient 15s ease infinite, colorChange 20s ease infinite;
        }
        
        /* Lluvia de logos */
        .logo-rain {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
            overflow: hidden;
        }
        
        .falling-logo {
            position: absolute;
            width: 40px;
            height: 40px;
            background-size: contain;
            background-repeat: no-repeat;
            background-position: center;
            opacity: 0.4;
            filter: brightness(1.2);
            animation: fall linear infinite;
        }
        
        @keyframes fall {
            from {
                transform: translateY(-100px) rotate(0deg);
            }
            to {
                transform: translateY(100vh) rotate(360deg);
            }
        }
        
        @keyframes gradient {
            0% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
            100% {
                background-position: 0% 50%;
            }
        }
        
        @keyframes colorChange {
            0% {
                filter: hue-rotate(0deg);
            }
            50% {
                filter: hue-rotate(180deg);
            }
            100% {
                filter: hue-rotate(360deg);
            }
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .header-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .logos-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo {
            width: 60px;
            height: 60px;
            background-color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: var(--primary);
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
            overflow: hidden;
        }
        
        .logo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .title-container {
            flex-grow: 1;
            text-align: center;
        }
        
        h1 {
            font-size: 2.2rem;
            margin-bottom: 0.5rem;
        }
        
        .subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1.5rem;
        }
        
        .search-container {
            margin-bottom: 2rem;
            display: flex;
            justify-content: center;
        }
        
        #search {
            width: 100%;
            max-width: 500px;
            padding: 12px 20px;
            border: 2px solid var(--secondary);
            border-radius: 30px;
            font-size: 1rem;
            outline: none;
            transition: all 0.3s;
            background-color: rgba(255, 255, 255, 0.8);
        }
        
        #search:focus {
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.3);
            background-color: white;
        }
        
        .languages-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-bottom: 3rem;
        }
        
        .language-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
            text-decoration: none;
            color: inherit;
            display: block;
        }
        
        .language-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
        }
        
        .card-header {
            padding: 1.2rem;
            color: white;
            text-align: center;
            position: relative;
            height: 120px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .language-logo {
            width: 60px;
            height: 60px;
            margin: 0 auto 10px;
            border-radius: 50%;
            overflow: hidden;
            background-color: white;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .language-logo img {
            width: 80%;
            height: 80%;
            object-fit: contain;
        }
        
        .card-body {
            padding: 1.2rem;
        }
        
        .language-name {
            font-size: 1.4rem;
            margin-bottom: 0.5rem;
        }
        
        .language-type {
            font-size: 0.9rem;
            opacity: 0.9;
            margin-bottom: 0.8rem;
        }
        
        .language-use {
            font-size: 0.95rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }
        
        footer {
            background: var(--primary);
            color: white;
            text-align: center;
            padding: 1.5rem;
            margin-top: 3rem;
        }
        
        /* Estilos del modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            overflow-y: auto;
            animation: fadeIn 0.3s ease;
        }
        
        .modal-content {
            background-color: white;
            margin: 2rem auto;
            width: 90%;
            max-width: 900px;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            animation: slideUp 0.4s ease;
            overflow: hidden;
        }
        
        .modal-header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 1.5rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-header h2 {
            margin: 0;
            font-size: 1.8rem;
        }
        
        .close-btn {
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background-color 0.3s;
        }
        
        .close-btn:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }
        
        .modal-body {
            padding: 2rem;
        }
        
        .language-image {
            width: 100%;
            max-width: 400px;
            margin: 0 auto 1.5rem;
            display: block;
            border-radius: 8px;
        }
        
        .details-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
        }
        
        .info-section {
            margin-bottom: 1.5rem;
        }
        
        .info-section h3 {
            margin-bottom: 0.5rem;
            color: var(--primary);
            border-bottom: 2px solid var(--secondary);
            padding-bottom: 0.3rem;
        }
        
        .info-section p {
            margin-bottom: 0.5rem;
        }
        
        .code-example {
            background: #2d2d2d;
            color: #f8f8f2;
            padding: 1.5rem;
            border-radius: 8px;
            font-family: 'Courier New', monospace;
            overflow-x: auto;
            margin-top: 1rem;
        }
        
        .info-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-top: 0.5rem;
        }
        
        .info-tag {
            background-color: var(--light);
            padding: 0.3rem 0.7rem;
            border-radius: 20px;
            font-size: 0.85rem;
            color: var(--dark);
        }
        
        /* Estilos para el juego */
        .game-section {
            background: white;
            border-radius: 10px;
            padding: 2rem;
            margin-bottom: 3rem;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            text-align: center;
        }
        
        .game-section h2 {
            color: var(--primary);
            margin-bottom: 1rem;
        }
        
        .game-section p {
            margin-bottom: 1.5rem;
            color: var(--dark);
        }
        
        .btn {
            background: linear-gradient(135deg, var(--secondary), var(--primary));
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 30px;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
        }
        
        .game-container {
            background: white;
            border-radius: 10px;
            padding: 2rem;
            margin-bottom: 3rem;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .game-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        .game-stats {
            display: flex;
            gap: 1rem;
            font-weight: bold;
            color: var(--primary);
        }
        
        .question-container {
            margin-bottom: 2rem;
            position: relative;
        }
        
        .question-text {
            font-size: 1.4rem;
            margin-bottom: 1.5rem;
            color: var(--primary);
        }
        
        .options-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }
        
        .option-btn {
            background: var(--light);
            border: 2px solid var(--secondary);
            padding: 1rem;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 1rem;
            position: relative;
            overflow: hidden;
        }
        
        .option-btn:hover {
            background: var(--secondary);
            color: white;
            transform: translateY(-3px);
        }
        
        .option-btn.correct {
            background: var(--success);
            color: white;
            border-color: var(--success);
            animation: pulseCorrect 0.6s ease;
        }
        
        .option-btn.incorrect {
            background: var(--accent);
            color: white;
            border-color: var(--accent);
            animation: shake 0.5s ease;
        }
        
        .game-feedback {
            margin-bottom: 1.5rem;
            font-weight: bold;
            font-size: 1.1rem;
            min-height: 30px;
        }
        
        .game-controls {
            display: flex;
            justify-content: center;
            gap: 1rem;
        }
        
        .results-container {
            text-align: center;
        }
        
        .results-title {
            font-size: 1.8rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }
        
        .score-display {
            font-size: 3rem;
            font-weight: bold;
            color: var(--secondary);
            margin-bottom: 1.5rem;
        }
        
        .results-message {
            font-size: 1.2rem;
            margin-bottom: 1.5rem;
        }
        
        .trophy {
            font-size: 4rem;
            margin-bottom: 1.5rem;
        }
        
        /* Animaciones para respuestas correctas e incorrectas */
        .feedback-animation {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 5rem;
            z-index: 1001;
            pointer-events: none;
            animation: fadeOut 1.5s ease forwards;
        }
        
        .correct-animation {
            color: var(--success);
            text-shadow: 0 0 20px rgba(46, 204, 113, 0.7);
        }
        
        .incorrect-animation {
            color: var(--accent);
            text-shadow: 0 0 20px rgba(231, 76, 60, 0.7);
        }
        
        @keyframes pulseCorrect {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); box-shadow: 0 0 20px rgba(46, 204, 113, 0.7); }
            100% { transform: scale(1); }
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            10%, 30%, 50%, 70%, 90% { transform: translateX(-5px); }
            20%, 40%, 60%, 80% { transform: translateX(5px); }
        }
        
        @keyframes fadeOut {
            0% { opacity: 1; transform: translate(-50%, -50%) scale(1); }
            70% { opacity: 1; transform: translate(-50%, -50%) scale(1.2); }
            100% { opacity: 0; transform: translate(-50%, -50%) scale(1.5); }
        }
        
        @keyframes confetti {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
        }
        
        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background-color: var(--success);
            opacity: 0;
            z-index: 1000;
            pointer-events: none;
            animation: confetti 2s ease forwards;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        /* Estilos para la sección Acerca de */
        .about-section {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 100;
        }
        
        .about-btn {
            background: rgba(52, 152, 219, 0.8);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 30px;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(5px);
        }
        
        .about-btn:hover {
            background: rgba(52, 152, 219, 0.9);
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.25);
        }
        
        .about-content {
            display: none;
            position: absolute;
            bottom: 60px;
            right: 0;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
            width: 300px;
            backdrop-filter: blur(10px);
            animation: slideUp 0.3s ease;
        }
        
        .about-content h3 {
            color: var(--primary);
            margin-bottom: 0.5rem;
            font-size: 1.2rem;
        }
        
        .about-content h4 {
            color: var(--secondary);
            margin-bottom: 1rem;
            font-size: 1rem;
        }
        
        .about-content ul {
            list-style-type: none;
            padding: 0;
        }
        
        .about-content li {
            padding: 0.5rem 0;
            border-bottom: 1px solid rgba(0, 0, 0, 0.1);
        }
        
        .about-content li:last-child {
            border-bottom: none;
        }
        
        /* Estilos para el Chatbot */
        .chatbot-section {
            position: fixed;
            bottom: 90px;
            right: 20px;
            z-index: 100;
        }
        
        .chatbot-btn {
            background: rgba(255, 165, 0, 0.8);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 30px;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(5px);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .chatbot-btn:hover {
            background: rgba(255, 165, 0, 0.9);
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.25);
        }
        
        .chatbot-content {
            display: none;
            position: absolute;
            bottom: 60px;
            right: 0;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
            width: 350px;
            height: 450px;
            backdrop-filter: blur(10px);
            animation: slideUp 0.3s ease;
            flex-direction: column;
            overflow: hidden;
        }
        
        .chatbot-header {
            background: rgba(255, 165, 0, 0.9);
            color: white;
            padding: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .chatbot-header h3 {
            margin: 0;
            font-size: 1.2rem;
        }
        
        .chatbot-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .message {
            max-width: 80%;
            padding: 10px 15px;
            border-radius: 18px;
            font-size: 0.9rem;
            line-height: 1.4;
        }
        
        .user-message {
            align-self: flex-end;
            background: rgba(255, 165, 0, 0.2);
            border-bottom-right-radius: 5px;
        }
        
        .bot-message {
            align-self: flex-start;
            background: rgba(52, 152, 219, 0.1);
            border-bottom-left-radius: 5px;
        }
        
        .chatbot-input {
            display: flex;
            padding: 15px;
            border-top: 1px solid rgba(0, 0, 0, 0.1);
            gap: 10px;
        }
        
        .chatbot-input input {
            flex: 1;
            padding: 10px 15px;
            border: 1px solid rgba(0, 0, 0, 0.2);
            border-radius: 20px;
            outline: none;
            font-size: 0.9rem;
        }
        
        .chatbot-input button {
            background: rgba(255, 165, 0, 0.8);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .chatbot-input button:hover {
            background: rgba(255, 165, 0, 0.9);
            transform: scale(1.05);
        }
        
        .typing-indicator {
            display: none;
            align-self: flex-start;
            background: rgba(52, 152, 219, 0.1);
            padding: 10px 15px;
            border-radius: 18px;
            border-bottom-left-radius: 5px;
            font-style: italic;
            color: #666;
        }
        
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            .logos-container {
                justify-content: center;
            }
            
            .languages-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
            
            .details-content {
                grid-template-columns: 1fr;
            }
            
            .modal-content {
                width: 95%;
                margin: 1rem auto;
            }
            
            .options-container {
                grid-template-columns: 1fr;
            }
            
            .feedback-animation {
                font-size: 3rem;
            }
            
            .about-section {
                bottom: 10px;
                right: 10px;
            }
            
            .about-content {
                width: 250px;
            }
            
            .chatbot-section {
                bottom: 80px;
                right: 10px;
            }
            
            .chatbot-content {
                width: 300px;
                height: 400px;
            }
        }
    </style>
</head>
<body>
    <div class="animated-background"></div>
    
    <!-- Contenedor para la lluvia de logos -->
    <div class="logo-rain" id="logoRain"></div>
    
    <header>
        <div class="header-content">
            <div class="logos-container">
                <div class="logo">
                    <img src="https://aulavirtual.cobaejescolar.edu.mx/pluginfile.php/1/core_admin/logocompact/300x300/1643482321/logoc.png" alt="Logo COBAEJ">
                </div>
            </div>
            
            <div class="title-container">
                <h1>Enciclopedia de Lenguajes de Programación</h1>
                <div class="subtitle">JORDAN Y SU EQUIPO</div>
            </div>
            
            <div class="logos-container">
                <div class="logo">
                    <img src="c:\Users\bobad\Downloads\WhatsApp Image 2025-10-19 at 17.38.25.jpeg" alt="Logo del equipo">
                </div>
            </div>
        </div>
    </header>
    
    <div class="container">
        <div class="search-container">
            <input type="text" id="search" placeholder="Buscar lenguaje de programación...">
        </div>
        
        <div class="languages-grid" id="languagesGrid">
            <!-- Las tarjetas de lenguajes se generarán con JavaScript -->
        </div>
        
        <!-- Sección del juego -->
        <div class="game-section">
            <h2>¿Eres un experto en lenguajes de programación?</h2>
            <p>Después de explorar todos los lenguajes, pon a prueba tus conocimientos con nuestro juego de trivia. Las preguntas se basan en la información que acabas de ver.</p>
            <button class="btn" id="startGameBtn">¡Comenzar Juego!</button>
        </div>
        
        <div class="game-container" id="gameContainer" style="display: none;">
            <div class="game-header">
                <div class="game-stats">
                    <div>Pregunta: <span id="currentQuestion">1</span>/<span id="totalQuestions">10</span></div>
                    <div>Puntaje: <span id="score">0</span></div>
                </div>
            </div>
            
            <div class="question-container">
                <div class="question-text" id="questionText"></div>
                
                <div class="options-container" id="optionsContainer">
                    <!-- Las opciones se generarán con JavaScript -->
                </div>
                
                <div class="game-feedback" id="gameFeedback"></div>
                
                <div class="game-controls">
                    <button class="btn" id="nextQuestionBtn" style="display: none;">Siguiente Pregunta</button>
                    <button class="btn" id="finishGameBtn" style="display: none;">Ver Resultados</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Sección Chatbot (fija en la parte inferior derecha) -->
    <div class="chatbot-section">
        <button class="chatbot-btn" id="chatbotBtn">
            <span>🤖</span> Asistente Virtual
        </button>
        <div class="chatbot-content" id="chatbotContent">
            <div class="chatbot-header">
                <span>🤖</span>
                <h3>Asistente Virtual</h3>
            </div>
            <div class="chatbot-messages" id="chatbotMessages">
                <div class="message bot-message">
                    ¡Hola! Soy tu asistente virtual. Puedes preguntarme sobre cualquier lenguaje de programación de esta enciclopedia. ¿En qué puedo ayudarte?
                </div>
            </div>
            <div class="typing-indicator" id="typingIndicator">El asistente está escribiendo...</div>
            <div class="chatbot-input">
                <input type="text" id="chatbotInput" placeholder="Escribe tu pregunta aquí...">
                <button id="sendMessageBtn">
                    <span>➤</span>
                </button>
            </div>
        </div>
    </div>
    
    <!-- Sección Acerca de (fija en la parte inferior derecha) -->
    <div class="about-section">
        <button class="about-btn" id="aboutBtn">Acerca de</button>
        <div class="about-content" id="aboutContent">
            <h3>Acerca de</h3>
            <h4>Integrantes del equipo:</h4>
            <ul>
                <li>Elizabeth Bobadilla Osaria</li>
                <li>Estefania Bobadilla Osoria</li>
                <li>Jordán Ledesma Álvarez</li>
                <li>Laura Uribe Osoria</li>
            </ul>
        </div>
    </div>
    
    <!-- Modal para mostrar detalles del lenguaje -->
    <div id="languageModal" class="modal">
        <div class="modal-content">
            <div class="modal-header" id="modalHeader">
                <h2 id="modalTitle">Título</h2>
                <button class="close-btn" id="closeModal">&times;</button>
            </div>
            <div class="modal-body" id="modalBody">
                <!-- El contenido del modal se llenará con JavaScript -->
            </div>
        </div>
    </div>
    
    <!-- Modal para mostrar resultados del juego -->
    <div id="resultsModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Resultados del Juego</h2>
                <button class="close-btn" id="closeResultsModal">&times;</button>
            </div>
            <div class="modal-body">
                <div class="results-container" id="resultsContainer">
                    <!-- Los resultados se generarán con JavaScript -->
                </div>
            </div>
        </div>
    </div>
    
    <footer>
        <p>JORDAN Y SU EQUIPO</p>
    </footer>

    <script>
        // Datos de los lenguajes de programación con información ampliada
        const languages = [
            {
                id: 1,
                name: "Swift",
                type: "Lenguaje de alto nivel, compilado",
                characteristic: "Desarrollado por Apple para ser seguro, rápido y expresivo.",
                commonUse: "Desarrollo de aplicaciones para iOS, macOS, watchOS y tvOS.",
                example: "print(\"Hola, mundo!\")",
                color: "#FF6B35",
                logo: "https://developer.apple.com/assets/elements/icons/swift/swift-64x64.png",
                image: "https://media.giphy.com/media/26tn33aiTi1jkl6H6/giphy.gif",
                description: "Swift es un lenguaje de programación potente e intuitivo creado por Apple para el desarrollo de aplicaciones para iOS, Mac, Apple TV y Apple Watch. Está diseñado para dar a los desarrolladores más libertad que nunca. Swift es fácil de usar y de código abierto, por lo que cualquier persona con una idea puede crear algo increíble.",
                year: 2014,
                creator: "Chris Lattner y Apple Inc.",
                paradigm: ["Orientado a objetos", "Protocol-oriented", "Funcional", "Imperativo"],
                typing: ["Estático", "Fuerte", "Inferencia de tipos"],
                influences: ["Objective-C", "Rust", "Haskell", "Ruby", "Python", "C#"],
                license: "Apache 2.0",
                version: "5.9",
                website: "https://swift.org"
            },
            {
                id: 2,
                name: "Ruby",
                type: "Lenguaje de alto nivel, interpretado",
                characteristic: "Enfocado en la simplicidad y productividad, con una sintaxis elegante.",
                commonUse: "Desarrollo web (especialmente con Ruby on Rails), scripting.",
                example: "puts 'Hola, mundo!'",
                color: "#CC342D",
                logo: "https://cdn.iconscout.com/icon/free/png-256/ruby-2752084-2284901.png",
                image: "https://imgs.search.brave.com/j4enJvUG0Vd-QKzHqXkdQnU8xymM5qcJoyL8iHRG98Y/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly93d3cu/ZGVzaWdudmVsb3Bl/ci5jb20vd3AtY29u/dGVudC91cGxvYWRz/LzIwMjMvMDEvd2hh/dC1pcy1ydWJ5LnBu/Zw",
                description: "Ruby es un lenguaje de programación dinámico y de código abierto centrado en la simplicidad y la productividad. Tiene una sintaxis elegante que es natural de leer y fácil de escribir. En Ruby, todo es un objeto, lo que permite un estilo de programación muy expresivo.",
                year: 1995,
                creator: "Yukihiro Matsumoto",
                paradigm: ["Orientado a objetos", "Imperativo", "Funcional", "Reflexivo"],
                typing: ["Dinámico", "Duck typing"],
                influences: ["Perl", "Smalltalk", "Eiffel", "Ada", "Lisp"],
                license: "Ruby License",
                version: "3.2.2",
                website: "https://www.ruby-lang.org"
            },
            {
                id: 3,
                name: "Python",
                type: "Lenguaje de alto nivel, interpretado",
                characteristic: "Enfatiza la legibilidad del código y su sintaxis clara.",
                commonUse: "Desarrollo web, ciencia de datos, IA, scripting, automatización.",
                example: "print(\"Hola, mundo!\")",
                color: "#3776AB",
                logo: "https://cdn.iconscout.com/icon/free/png-256/python-2-226051.png",
                image: "https://media.giphy.com/media/KAq5w47R9rmTuvWOWa/giphy.gif",
                description: "Python es un lenguaje de programación interpretado cuya filosofía hace hincapié en la legibilidad de su código. Se trata de un lenguaje de programación multiparadigma, ya que soporta orientación a objetos, programación imperativa y, en menor medida, programación funcional.",
                year: 1991,
                creator: "Guido van Rossum",
                paradigm: ["Multiparadigma", "Orientado a objetos", "Imperativo", "Funcional", "Procedural"],
                typing: ["Dinámico", "Fuerte", "Duck typing"],
                influences: ["ABC", "Modula-3", "C", "C++", "ALGOL 68", "Unix shell"],
                license: "Python Software Foundation License",
                version: "3.12.0",
                website: "https://www.python.org"
            },
            {
                id: 4,
                name: "Java",
                type: "Lenguaje de alto nivel, compilado a bytecode",
                characteristic: "Diseñado para ser portable con el eslogan 'write once, run anywhere'.",
                commonUse: "Aplicaciones empresariales, Android, sistemas grandes.",
                example: "System.out.println(\"Hola, mundo!\");",
                color: "#ED8B00",
                logo: "https://cdn.iconscout.com/icon/free/png-256/java-43-569305.png",
                image: "https://imgs.search.brave.com/NlNK5uV9ZXTddHcmTbEpeOTNZEZku5BXvIjiWnSPDkY/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly9jZG4u/dGhlbmV3c3RhY2su/aW8vbWVkaWEvMjAy/NC8wMy9kNTI0MGFm/Zi1qYXZhLWhvcnot/Y2xyLTEtMTAyNHg2/NzItY29weS5wbmc",
                description: "Java es un lenguaje de programación y una plataforma informática comercializada por primera vez en 1995 por Sun Microsystems. Hay muchas aplicaciones y sitios web que no funcionarán a menos que tenga Java instalado, y cada día se crean más. Java es rápido, seguro y fiable.",
                year: 1995,
                creator: "James Gosling (Sun Microsystems)",
                paradigm: ["Orientado a objetos", "Estructurado", "Imperativo", "Genérico", "Reflexivo"],
                typing: ["Estático", "Fuerte", "Seguro", "Nominativo"],
                influences: ["C++", "C", "Objective-C", "Smalltalk"],
                license: "GNU GPL v2",
                version: "Java 21",
                website: "https://www.java.com"
            },
            {
                id: 5,
                name: "JavaScript",
                type: "Lenguaje de alto nivel, interpretado",
                characteristic: "Lenguaje de scripting para páginas web, ahora usado también en servidor.",
                commonUse: "Desarrollo web frontend y backend (Node.js), aplicaciones móviles.",
                example: "console.log('Hola, mundo!');",
                color: "#F7DF1E",
                logo: "https://cdn.iconscout.com/icon/free/png-256/javascript-1-225993.png",
                image: "https://media.giphy.com/media/xT9IgzoKnwFNmISR8I/giphy.gif",
                description: "JavaScript es un lenguaje de programación ligero, interpretado, o compilado justo-a-tiempo (JIT) con funciones de primera clase. Si bien es más conocido como un lenguaje de scripting para páginas web, es usado en muchos entornos fuera del navegador.",
                year: 1995,
                creator: "Brendan Eich (Netscape)",
                paradigm: ["Multiparadigma", "Funcional", "Orientado a objetos", "Basado en prototipos", "Imperativo"],
                typing: ["Dinámico", "Débil", "Duck typing"],
                influences: ["Java", "Scheme", "Self", "AWK", "HyperTalk"],
                license: "MIT License",
                version: "ECMAScript 2023",
                website: "https://developer.mozilla.org/es/docs/Web/JavaScript"
            },
            {
                id: 6,
                name: "PHP",
                type: "Lenguaje de scripting del lado del servidor",
                characteristic: "Diseñado específicamente para el desarrollo web.",
                commonUse: "Desarrollo web del lado del servidor.",
                example: `<?php
// Ejemplo básico de PHP
$mensaje = "Hola, mundo!";
echo $mensaje;

// Ejemplo con función
function saludar($nombre) {
    return "¡Hola, " . $nombre . "!";
}

echo saludar("Mundo");
?>`,
                color: "#777BB4",
                logo: "https://cdn.iconscout.com/icon/free/png-256/php-27-226043.png",
                image: "https://imgs.search.brave.com/7H33OMAb8F4ai7-RQDOhaIqM5b2EyJb7c5Wc6QkWU4Q/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly9tZWRp/YS5pc3RvY2twaG90/by5jb20vaWQvMTI5/Nzc1Mjk5NC9waG90/by9waHAtaW5zY3Jp/cHRpb24tYWdhaW5z/dC1sYXB0b3AtYW5k/LWNvZGUtYmFja2dy/b3VuZC1sZWFybi1w/aHAtcHJvZ3JhbW1p/bmctbGFuZ3VhZ2Ut/Y29tcHV0ZXIuanBn/P2I9MSZzPTYxMng2/MTImdz0wJms9MjAm/Yz1ycDdhem0tSFA4/SnNSd0dib2pyVmND/Z0tjYjRyeU9CSDhy/aUk2ZXRzRkZjPQ",
                description: "PHP es un lenguaje de scripting de uso general que se adapta especialmente al desarrollo web. Fue creado inicialmente por el programador danés-canadiense Rasmus Lerdorf en 1994. El código PHP generalmente es procesado en un servidor web por un intérprete PHP implementado como un módulo, un daemon o como un ejecutable CGI.",
                year: 1995,
                creator: "Rasmus Lerdorf",
                paradigm: ["Imperativo", "Orientado a objetos", "Funcional", "Procedural", "Reflexivo"],
                typing: ["Dinámico", "Débil"],
                influences: ["Perl", "C", "C++", "Java", "Tcl"],
                license: "PHP License",
                version: "8.2.12",
                website: "https://www.php.net"
            },
            {
                id: 7,
                name: "HTML",
                type: "Lenguaje de marcado (no de programación)",
                characteristic: "Define la estructura y el contenido de una página web.",
                commonUse: "Desarrollo web (estructura de páginas).",
                example: "<h1>Hola, mundo!</h1>",
                color: "#E34F26",
                logo: "https://cdn.iconscout.com/icon/free/png-256/html5-40-1175193.png",
                image: "https://media.giphy.com/media/XAxylRMCdpbEWUAvr8/giphy.gif",
                description: "HTML, siglas en inglés de HyperText Markup Language, hace referencia al lenguaje de marcado para la elaboración de páginas web. Es un estándar que sirve de referencia del software que conecta con la elaboración de páginas web en sus diferentes versiones.",
                year: 1993,
                creator: "Tim Berners-Lee",
                paradigm: ["Lenguaje de marcado"],
                typing: ["No aplica"],
                influences: ["SGML"],
                license: "Estándar W3C",
                version: "HTML5",
                website: "https://developer.mozilla.org/es/docs/Web/HTML"
            },
            {
                id: 8,
                name: "CSS",
                type: "Lenguaje de hojas de estilo (no de programación)",
                characteristic: "Define el estilo y presentación de documentos HTML.",
                commonUse: "Desarrollo web (diseño y estilo de páginas).",
                example: "body { font-family: Arial; color: #333; }",
                color: "#1572B6",
                logo: "https://cdn.iconscout.com/icon/free/png-256/css3-11-1175239.png",
                image: "https://imgs.search.brave.com/sHUDFKmWfe52ej8Ua782Z8fJO3_RPVhFFq2ewSngHgU/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly93d3cu/ZGlnaXRhbG9jZWFu/LmNvbS9hcGkvc3Rh/dGljLWNvbnRlbnQv/djEvaW1hZ2VzP3Ny/Yz1odHRwczovL2Nv/bW11bml0eS1jZG4t/ZGlnaXRhbG9jZWFu/LWNvbS5nbG9iYWwu/c3NsLmZhc3RseS5u/ZXQvR0NlYnVGdUFa/aFFXdndWc0tjTXpl/UXA0JndpZHRoPTE5/MjA",
                description: "CSS, en español «Hojas de estilo en cascada», es un lenguaje de diseño gráfico para definir y crear la presentación de un documento estructurado escrito en un lenguaje de marcado. Es muy usado para establecer el diseño visual de los documentos web, e interfaces de usuario escritas en HTML.",
                year: 1996,
                creator: "Håkon Wium Lie, Bert Bos",
                paradigm: ["Lenguaje de hojas de estilo"],
                typing: ["No aplica"],
                influences: ["DSSSL"],
                license: "Estándar W3C",
                version: "CSS3",
                website: "https://developer.mozilla.org/es/docs/Web/CSS"
            },
            {
                id: 9,
                name: "C++",
                type: "Lenguaje de medio/alto nivel, compilado",
                characteristic: "Extensión de C con programación orientada a objetos.",
                commonUse: "Sistemas operativos, juegos, aplicaciones de alto rendimiento.",
                example: "#include <iostream>\nint main() {\n  std::cout << \"Hola, mundo!\";\n  return 0;\n}",
                color: "#00599C",
                logo: "https://cdn.iconscout.com/icon/free/png-256/c-4-226082.png",
                image: "https://imgs.search.brave.com/JlQSFLHrRRudXNiMV-n-q1T2XQKbzyhJ5MjNiYkvas4/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly93d3cu/c2h1dHRlcnN0b2Nr/LmNvbS9pbWFnZS1w/aG90by9jLXByb2dy/YW1taW5nLWxhbmd1/YWdlLWxldHRlcmlu/Zy1tYW4tMjYwbnct/MjExMjYxMjU0Mi5q/cGc",
                description: "C++ es un lenguaje de programación diseñado en 1979 por Bjarne Stroustrup. La intención de su creación fue extender al lenguaje de programación C mecanismos que permiten la manipulación de objetos. En ese sentido, desde el point de vista de los lenguajes orientados a objetos, C++ es un lenguaje híbrido.",
                year: 1985,
                creator: "Bjarne Stroustrup",
                paradigm: ["Multiparadigma", "Orientado a objetos", "Procedural", "Genérico", "Funcional"],
                typing: ["Estático", "Fuerte", "Nominativo", "Inferencia parcial"],
                influences: ["C", "Simula", "ALGOL 68", "Ada", "CLU", "ML"],
                license: "Licencia propietaria",
                version: "C++23",
                website: "https://isocpp.org"
            },
            {
                id: 10,
                name: "C#",
                type: "Lenguaje de alto nivel, compilado",
                characteristic: "Desarrollado por Microsoft, similar a Java pero para el ecosistema .NET.",
                commonUse: "Desarrollo de aplicaciones Windows, videojuegos (Unity), web.",
                example: "Console.WriteLine(\"Hola, mundo!\");",
                color: "#239120",
                logo: "https://imgs.search.brave.com/n--a-ahS3IIC22ZKL1l4CVM6tCAvJDfN97cIEkioNCY/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly9jZG4u/d29ybGR2ZWN0b3Js/b2dvLmNvbS9sb2dv/cy9jLS00LnN2Zw",
                image: "https://imgs.search.brave.com/xjDgIgfZblp4q5bvUBJD5eeWq5qP6u-M770lywGTweM/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly9jZG4u/dGhlbmV3c3RhY2su/aW8vbWVkaWEvMjAy/NS8wMS8zNGUzYjBl/My1jLWludHJvZHVj/dGlvbi5qcGc",
                description: "C# es un lenguaje de programación multiparadigma desarrollado y estandarizado por Microsoft como parte de su plataforma .NET, que después fue aprobado como un estándar por la ECMA e ISO. C# es uno de los lenguajes de programación diseñados para la infraestructura de lenguaje común.",
                year: 2000,
                creator: "Microsoft (Anders Hejlsberg)",
                paradigm: ["Multiparadigma", "Orientado a objetos", "Estructurado", "Imperativo", "Genérico", "Reflexivo"],
                typing: ["Estático", "Dinámico parcial", "Fuerte", "Seguro", "Nominativo"],
                influences: ["C++", "Java", "Delphi", "Modula-3", "Smalltalk"],
                license: "MIT/X11",
                version: "12.0",
                website: "https://dotnet.microsoft.com/es-es/languages/csharp"
            },
            {
                id: 11,
                name: "C",
                type: "Lenguaje de programación de propósito general, compilado",
                characteristic: "Lenguaje de nivel medio que combina elementos de lenguaje de alto nivel con la funcionalidad de lenguaje ensamblador.",
                commonUse: "Sistemas operativos, compiladores, sistemas embebidos, aplicaciones de alto rendimiento.",
                example: "#include <stdio.h>\nint main() {\n  printf(\"Hola, mundo!\");\n  return 0;\n}",
                color: "#A8B9CC",
                logo: "https://cdn.iconscout.com/icon/free/png-256/c-57-1175191.png",
                image: "https://media.giphy.com/media/26tn33aiTi1jkl6H6/giphy.gif",
                description: "C es un lenguaje de programación de propósito general originalmente desarrollado por Dennis Ritchie entre 1969 y 1972 en los Laboratorios Bell, como evolución del anterior lenguaje B, a su vez basado en BCPL. Al igual que B, es un lenguaje orientado a la implementación de sistemas operativos, concretamente Unix.",
                year: 1972,
                creator: "Dennis Ritchie (Bell Labs)",
                paradigm: ["Imperativo", "Procedural", "Estructurado"],
                typing: ["Estático", "Débil", "Manifiesto"],
                influences: ["B", "BCPL", "ALGOL 68", "Assembler"],
                license: "Sin licencia específica (dominio público)",
                version: "C18 (ISO/IEC 9899:2018)",
                website: "https://www.iso.org/standard/74528.html"
            }
        ];

        // Resto del código JavaScript permanece igual...
        // Referencias a elementos del DOM
        const languagesGrid = document.getElementById('languagesGrid');
        const searchInput = document.getElementById('search');
        const languageModal = document.getElementById('languageModal');
        const modalTitle = document.getElementById('modalTitle');
        const modalBody = document.getElementById('modalBody');
        const closeModal = document.getElementById('closeModal');
        const modalHeader = document.getElementById('modalHeader');
        const startGameBtn = document.getElementById('startGameBtn');
        const gameContainer = document.getElementById('gameContainer');
        const questionText = document.getElementById('questionText');
        const optionsContainer = document.getElementById('optionsContainer');
        const gameFeedback = document.getElementById('gameFeedback');
        const nextQuestionBtn = document.getElementById('nextQuestionBtn');
        const finishGameBtn = document.getElementById('finishGameBtn');
        const currentQuestion = document.getElementById('currentQuestion');
        const totalQuestions = document.getElementById('totalQuestions');
        const score = document.getElementById('score');
        const resultsModal = document.getElementById('resultsModal');
        const resultsContainer = document.getElementById('resultsContainer');
        const closeResultsModal = document.getElementById('closeResultsModal');
        const aboutBtn = document.getElementById('aboutBtn');
        const aboutContent = document.getElementById('aboutContent');
        const chatbotBtn = document.getElementById('chatbotBtn');
        const chatbotContent = document.getElementById('chatbotContent');
        const chatbotMessages = document.getElementById('chatbotMessages');
        const chatbotInput = document.getElementById('chatbotInput');
        const sendMessageBtn = document.getElementById('sendMessageBtn');
        const typingIndicator = document.getElementById('typingIndicator');

        // Variables del juego
        let currentQuestionIndex = 0;
        let userScore = 0;
        let selectedOption = null;
        let gameStarted = false;
        let quizQuestions = [];

        // Preguntas específicas basadas en la información de los lenguajes
        const languageSpecificQuestions = [
            // Swift
            {
                question: "¿Qué empresa desarrolló Swift y para qué plataformas está destinado principalmente?",
                options: [
                    "Microsoft para Windows",
                    "Apple para iOS, macOS, watchOS y tvOS", 
                    "Google para Android",
                    "Oracle para aplicaciones empresariales"
                ],
                correct: 1,
                explanation: "Swift fue desarrollado por Apple específicamente para sus plataformas: iOS, macOS, watchOS y tvOS."
            },
            {
                question: "¿Qué característica principal distingue a Swift según su descripción?",
                options: [
                    "Ser el lenguaje más antiguo",
                    "Ser seguro, rápido y expresivo",
                    "Ser exclusivamente para web",
                    "No tener tipos de datos"
                ],
                correct: 1,
                explanation: "Swift fue diseñado por Apple para ser seguro, rápido y expresivo como sus características principales."
            },
            
            // Ruby
            {
                question: "¿En qué se enfoca principalmente Ruby según su descripción?",
                options: [
                    "Velocidad de ejecución máxima",
                    "Bajo consumo de memoria", 
                    "Simplicidad y productividad",
                    "Programación a bajo nivel"
                ],
                correct: 2,
                explanation: "Ruby se enfoca en la simplicidad y productividad, con una sintaxis elegante que es natural de leer."
            },
            {
                question: "¿Qué concepto fundamental de Ruby permite que 'todo es un objeto'?",
                options: [
                    "Programación orientada a objetos pura",
                    "Programación funcional",
                    "Programación procedural",
                    "Programación lógica"
                ],
                correct: 0,
                explanation: "En Ruby, todo es un objeto, lo que permite un estilo de programación muy expresivo."
            },
            
            // Python
            {
                question: "¿Qué enfatiza Python según su filosofía de diseño?",
                options: [
                    "La velocidad de compilación",
                    "La legibilidad del código",
                    "El bajo nivel de abstracción", 
                    "La programación orientada a clases"
                ],
                correct: 1,
                explanation: "Python enfatiza la legibilidad del código y su sintaxis clara como parte fundamental de su filosofía."
            },
            {
                question: "¿Para qué áreas es comúnmente usado Python?",
                options: [
                    "Solo desarrollo web",
                    "Solo inteligencia artificial",
                    "Desarrollo web, ciencia de datos, IA y automatización",
                    "Sistemas operativos"
                ],
                correct: 2,
                explanation: "Python se usa en desarrollo web, ciencia de datos, IA, scripting y automatización por su versatilidad."
            },
            
            // Java
            {
                question: "¿Con qué famoso eslogan se diseñó Java?",
                options: [
                    "'Fast and furious'",
                    "'Write once, run anywhere'", 
                    "'Code less, do more'",
                    "'Power to the developers'"
                ],
                correct: 1,
                explanation: "Java fue diseñado con el eslogan 'write once, run anywhere' (escribe una vez, ejecuta en cualquier lugar)."
            },
            {
                question: "¿Qué tipo de aplicaciones son el uso común de Java?",
                options: [
                    "Solo aplicaciones móviles",
                    "Solo aplicaciones web",
                    "Aplicaciones empresariales, Android y sistemas grandes",
                    "Solo videojuegos"
                ],
                correct: 2,
                explanation: "Java se usa comúnmente para aplicaciones empresariales, Android y sistemas grandes."
            },
            
            // JavaScript
            {
                question: "¿Para qué fue diseñado originalmente JavaScript?",
                options: [
                    "Aplicaciones de escritorio",
                    "Scripting para páginas web", 
                    "Bases de datos",
                    "Sistemas operativos"
                ],
                correct: 1,
                explanation: "JavaScript fue diseñado originalmente como lenguaje de scripting para páginas web."
            },
            {
                question: "¿Qué permite JavaScript además del desarrollo frontend?",
                options: [
                    "Desarrollo de drivers",
                    "Programación de hardware",
                    "Desarrollo backend con Node.js",
                    "Compilación a código máquina"
                ],
                correct: 2,
                explanation: "JavaScript ahora también se usa en el backend con Node.js, no solo en frontend."
            },
            
            // PHP
            {
                question: "¿Para qué fue diseñado específicamente PHP?",
                options: [
                    "Aplicaciones móviles",
                    "Inteligencia artificial",
                    "Desarrollo web del lado del servidor", 
                    "Aplicaciones de escritorio"
                ],
                correct: 2,
                explanation: "PHP fue diseñado específicamente para el desarrollo web del lado del servidor."
            },
            
            // HTML y CSS
            {
                question: "¿Qué define principalmente HTML?",
                options: [
                    "El estilo de las páginas",
                    "La estructura y contenido de las páginas web", 
                    "La interactividad",
                    "La lógica de negocio"
                ],
                correct: 1,
                explanation: "HTML define la estructura y el contenido de una página web."
            },
            {
                question: "¿Qué función principal tiene CSS?",
                options: [
                    "Definir la estructura de la página",
                    "Agregar interactividad",
                    "Definir el estilo y presentación de documentos HTML", 
                    "Manejar bases de datos"
                ],
                correct: 2,
                explanation: "CSS define el estilo y presentación de documentos HTML."
            },
            
            // C++
            {
                question: "¿Qué añade C++ al lenguaje C?",
                options: [
                    "Solo mejor rendimiento",
                    "Solo más tipos de datos",
                    "Programación orientada a objetos", 
                    "Solo sintaxis más simple"
                ],
                correct: 2,
                explanation: "C++ es una extensión de C que añade programación orientada a objetos."
            },
            
            // C#
            {
                question: "¿Qué empresa desarrolló C# y para qué plataforma?",
                options: [
                    "Apple para macOS",
                    "Google para Android", 
                    "Microsoft para .NET",
                    "Oracle para Java"
                ],
                correct: 2,
                explanation: "C# fue desarrollado por Microsoft para su ecosistema .NET."
            },
            
            // C
            {
                question: "¿Dónde y cuándo fue desarrollado el lenguaje C?",
                options: [
                    "Microsoft en 1995",
                    "Bell Labs entre 1969 y 1972", 
                    "Apple en 1984",
                    "IBM en 1975"
                ],
                correct: 1,
                explanation: "C fue desarrollado por Dennis Ritchie en los Laboratorios Bell entre 1969 y 1972."
            },
            {
                question: "¿Para qué propósito fue diseñado originalmente C?",
                options: [
                    "Desarrollo web",
                    "Inteligencia artificial",
                    "Implementación del sistema operativo Unix", 
                    "Aplicaciones móviles"
                ],
                correct: 2,
                explanation: "C fue diseñado originalmente para la implementación del sistema operativo Unix."
            },
            {
                question: "¿Qué caracteriza a C como lenguaje de 'nivel medio'?",
                options: [
                    "Es más fácil que Python",
                    "Combina elementos de alto nivel con funcionalidad de ensamblador", 
                    "Solo se usa para aplicaciones web",
                    "No permite programación estructurada"
                ],
                correct: 1,
                explanation: "C se considera un lenguaje de nivel medio porque combina elementos de lenguaje de alto nivel con la funcionalidad de lenguaje ensamblador."
            }
        ];

        // Base de conocimientos para el chatbot
        const chatbotKnowledge = {
            "hola": ["¡Hola! ¿En qué puedo ayudarte hoy?", "¡Hola! ¿Tienes alguna pregunta sobre lenguajes de programación?"],
            "adiós": ["¡Hasta luego! Si tienes más preguntas, aquí estaré.", "¡Adiós! Espero haberte ayudado."],
            "gracias": ["¡De nada! Estoy aquí para ayudarte.", "¡No hay problema! ¿Algo más en lo que pueda ayudarte?"],
            "qué lenguajes conoces": ["Conozco información sobre todos los lenguajes que aparecen en esta enciclopedia: Swift, Ruby, Python, Java, JavaScript, PHP, HTML, CSS, C++, C# y C."],
            "ayuda": ["Puedo responder preguntas sobre los lenguajes de programación de esta enciclopedia. Por ejemplo, puedes preguntarme sobre sus características, usos, creadores, año de creación, etc."],
            "swift": ["Swift es un lenguaje desarrollado por Apple en 2014 para crear aplicaciones en iOS, macOS, watchOS y tvOS. Es seguro, rápido y expresivo.", "Swift fue creado por Chris Lattner y Apple. Se caracteriza por ser un lenguaje moderno y seguro para el desarrollo en el ecosistema Apple."],
            "ruby": ["Ruby es un lenguaje de programación dinámico creado por Yukihiro Matsumoto en 1995. Se enfoca en la simplicidad y productividad.", "Ruby es conocido por su elegante sintaxis y por ser el lenguaje detrás del framework Ruby on Rails para desarrollo web."],
            "python": ["Python es un lenguaje interpretado creado por Guido van Rossum en 1991. Enfatiza la legibilidad del código y es muy versátil.", "Python es ampliamente usado en desarrollo web, ciencia de datos, inteligencia artificial, scripting y automatización."],
            "java": ["Java es un lenguaje compilado a bytecode creado por James Gosling en Sun Microsystems en 1995. Sigue el principio 'write once, run anywhere'.", "Java es popular para aplicaciones empresariales, desarrollo Android y sistemas de gran escala."],
            "javascript": ["JavaScript es un lenguaje de scripting creado por Brendan Eich en 1995. Originalmente para páginas web, ahora también se usa en servidor con Node.js.", "JavaScript es el lenguaje principal para desarrollo web frontend y también se usa en backend con Node.js."],
            "php": ["PHP es un lenguaje de scripting del lado del servidor creado por Rasmus Lerdorf en 1995. Especializado en desarrollo web.", "PHP es muy popular para desarrollo web del lado del servidor, especialmente con sistemas como WordPress."],
            "html": ["HTML no es un lenguaje de programación, sino de marcado. Creado por Tim Berners-Lee en 1993, define la estructura de páginas web.", "HTML (HyperText Markup Language) es el lenguaje fundamental para crear páginas web."],
            "css": ["CSS no es un lenguaje de programación, sino de hojas de estilo. Creado por Håkon Wium Lie y Bert Bos en 1996, define el estilo de documentos HTML.", "CSS (Cascading Style Sheets) se usa para dar estilo y diseño a las páginas web."],
            "c++": ["C++ es una extensión de C con programación orientada a objetos, creado por Bjarne Stroustrup en 1985. Es usado en sistemas operativos, juegos y aplicaciones de alto rendimiento.", "C++ es conocido por su alto rendimiento y se usa en aplicaciones que requieren mucha potencia como videojuegos y sistemas operativos."],
            "c#": ["C# es un lenguaje desarrollado por Microsoft en 2000 para la plataforma .NET. Similar a Java, se usa en aplicaciones Windows, videojuegos (Unity) y web.", "C# es el lenguaje principal para desarrollo en el ecosistema Microsoft .NET."],
            "c": ["C es un lenguaje de propósito general creado por Dennis Ritchie en Bell Labs entre 1969-1972. Es considerado un lenguaje de nivel medio y se usa en sistemas operativos, compiladores y sistemas embebidos.", "C es uno de los lenguajes más influyentes y se usa como base para sistemas operativos como Unix y Linux."]
        };

        // Función para crear la lluvia de logos
        function createLogoRain() {
            const logoRain = document.getElementById('logoRain');
            const logoCount = 15; // Número de logos que caen simultáneamente
            
            // Crear logos que caen
            for (let i = 0; i < logoCount; i++) {
                setTimeout(() => {
                    createFallingLogo();
                    // Crear un nuevo logo periódicamente
                    setInterval(createFallingLogo, 2000);
                }, i * 500);
            }
        }
        
        function createFallingLogo() {
            const logoRain = document.getElementById('logoRain');
            const fallingLogo = document.createElement('div');
            fallingLogo.className = 'falling-logo';
            
            // Seleccionar un logo aleatorio
            const randomLanguage = languages[Math.floor(Math.random() * languages.length)];
            fallingLogo.style.backgroundImage = `url('${randomLanguage.logo}')`;
            
            // Posición horizontal aleatoria
            const leftPosition = Math.random() * 100;
            fallingLogo.style.left = `${leftPosition}%`;
            
            // Duración y retraso aleatorios para variar la velocidad
            const duration = 10 + Math.random() * 20; // Entre 10 y 30 segundos
            const delay = Math.random() * 5; // Retraso inicial aleatorio
            
            fallingLogo.style.animationDuration = `${duration}s`;
            fallingLogo.style.animationDelay = `${delay}s`;
            
            // Tamaño aleatorio
            const size = 20 + Math.random() * 30; // Entre 20px y 50px
            fallingLogo.style.width = `${size}px`;
            fallingLogo.style.height = `${size}px`;
            
            // Opacidad aleatoria
            const opacity = 0.2 + Math.random() * 0.3; // Entre 0.2 y 0.5
            fallingLogo.style.opacity = opacity;
            
            logoRain.appendChild(fallingLogo);
            
            // Eliminar el logo después de que termine su animación
            setTimeout(() => {
                if (fallingLogo.parentNode) {
                    fallingLogo.parentNode.removeChild(fallingLogo);
                }
            }, (duration + delay) * 1000);
        }

        // Función para mostrar animación de respuesta
        function showFeedbackAnimation(isCorrect) {
            const animation = document.createElement('div');
            animation.className = `feedback-animation ${isCorrect ? 'correct-animation' : 'incorrect-animation'}`;
            animation.textContent = isCorrect ? '✓' : '✗';
            
            document.body.appendChild(animation);
            
            // Crear confetti para respuestas correctas
            if (isCorrect) {
                createConfetti();
            }
            
            // Eliminar la animación después de que termine
            setTimeout(() => {
                document.body.removeChild(animation);
            }, 1500);
        }
        
        // Función para crear confetti
        function createConfetti() {
            const colors = ['#2ecc71', '#3498db', '#9b59b6', '#e74c3c', '#f1c40f', '#1abc9c'];
            
            for (let i = 0; i < 50; i++) {
                setTimeout(() => {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti';
                    confetti.style.left = `${Math.random() * 100}%`;
                    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                    confetti.style.width = `${5 + Math.random() * 10}px`;
                    confetti.style.height = `${5 + Math.random() * 10}px`;
                    confetti.style.borderRadius = Math.random() > 0.5 ? '50%' : '0';
                    confetti.style.animationDelay = `${Math.random() * 0.5}s`;
                    
                    document.body.appendChild(confetti);
                    
                    // Eliminar el confetti después de la animación
                    setTimeout(() => {
                        if (confetti.parentNode) {
                            confetti.parentNode.removeChild(confetti);
                        }
                    }, 2000);
                }, i * 20);
            }
        }

        // Función para mezclar un array (algoritmo Fisher-Yates)
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }

        // Función para mostrar las tarjetas de lenguajes
        function displayLanguages(languagesToShow = languages) {
            languagesGrid.innerHTML = '';
            
            languagesToShow.forEach(language => {
                const card = document.createElement('div');
                card.className = 'language-card';
                card.setAttribute('data-id', language.id);
                card.innerHTML = `
                    <div class="card-header" style="background-color: ${language.color}">
                        <div class="language-logo">
                            <img src="${language.logo}" alt="Logo de ${language.name}">
                        </div>
                        <h3 class="language-name">${language.name}</h3>
                    </div>
                    <div class="card-body">
                        <p class="language-type">${language.type}</p>
                        <p class="language-use">${language.commonUse}</p>
                        <p class="click-hint">Haz clic para ver detalles</p>
                    </div>
                `;
                
                // Agregar event listener a toda la tarjeta
                card.addEventListener('click', function() {
                    const languageId = parseInt(this.getAttribute('data-id'));
                    openLanguageModal(languageId);
                });
                
                languagesGrid.appendChild(card);
            });
        }

        // Función para abrir el modal con detalles del lenguaje
        function openLanguageModal(languageId) {
            // Buscar el lenguaje por ID
            const language = languages.find(lang => lang.id === languageId);
            
            if (language) {
                // Configurar el contenido del modal
                modalTitle.textContent = language.name;
                modalHeader.style.background = `linear-gradient(135deg, ${language.color}, ${adjustColor(language.color, 20)})`;
                
                // Crear etiquetas para paradigmas, sistema de tipos e influencias
                const paradigmsHTML = language.paradigm.map(p => `<span class="info-tag">${p}</span>`).join('');
                const typingHTML = language.typing.map(t => `<span class="info-tag">${t}</span>`).join('');
                const influencesHTML = language.influences.map(i => `<span class="info-tag">${i}</span>`).join('');
                
                modalBody.innerHTML = `
                    <img src="${language.image}" alt="${language.name}" class="language-image">
                    <div class="details-content">
                        <div>
                            <div class="info-section">
                                <h3>Descripción</h3>
                                <p>${language.description}</p>
                            </div>
                            
                            <div class="info-section">
                                <h3>Información Técnica</h3>
                                <p><strong>Año de creación:</strong> ${language.year}</p>
                                <p><strong>Creador(es):</strong> ${language.creator}</p>
                                <p><strong>Versión estable:</strong> ${language.version}</p>
                                <p><strong>Licencia:</strong> ${language.license}</p>
                                <p><strong>Sitio web:</strong> <a href="${language.website}" target="_blank">${language.website}</a></p>
                            </div>
                            
                            <div class="info-section">
                                <h3>Paradigmas de Programación</h3>
                                <div class="info-tags">
                                    ${paradigmsHTML}
                                </div>
                            </div>
                            
                            <div class="info-section">
                                <h3>Sistema de Tipos</h3>
                                <div class="info-tags">
                                    ${typingHTML}
                                </div>
                            </div>
                        </div>
                        <div>
                            <div class="info-section">
                                <h3>Característica Principal</h3>
                                <p>${language.characteristic}</p>
                            </div>
                            
                            <div class="info-section">
                                <h3>Uso Común</h3>
                                <p>${language.commonUse}</p>
                            </div>
                            
                            <div class="info-section">
                                <h3>Lenguajes que lo Influenciaron</h3>
                                <div class="info-tags">
                                    ${influencesHTML}
                                </div>
                            </div>
                            
                            <div class="info-section">
                                <h3>Ejemplo de Código</h3>
                                <div class="code-example">
                                    <pre>${language.example}</pre>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
                
                // Mostrar el modal
                languageModal.style.display = 'block';
            }
        }

        // Función auxiliar para ajustar el color (clarear)
        function adjustColor(color, amount) {
            return '#' + color.replace(/^#/, '').replace(/../g, color => ('0'+Math.min(255, Math.max(0, parseInt(color, 16) + amount)).toString(16)).substr(-2));
        }

        // Función para buscar lenguajes
        function searchLanguages() {
            const searchTerm = searchInput.value.toLowerCase();
            const filteredLanguages = languages.filter(language => 
                language.name.toLowerCase().includes(searchTerm) ||
                language.type.toLowerCase().includes(searchTerm) ||
                language.commonUse.toLowerCase().includes(searchTerm) ||
                language.creator.toLowerCase().includes(searchTerm) ||
                language.paradigm.some(p => p.toLowerCase().includes(searchTerm))
            );
            
            displayLanguages(filteredLanguages);
        }

        // Funciones del juego
        function startGame() {
            gameStarted = true;
            currentQuestionIndex = 0;
            userScore = 0;
            selectedOption = null;
            
            // Mezclar preguntas y seleccionar 10
            quizQuestions = shuffleArray([...languageSpecificQuestions]).slice(0, 10);
            
            document.querySelector('.game-section').style.display = 'none';
            gameContainer.style.display = 'block';
            
            totalQuestions.textContent = quizQuestions.length;
            updateScore();
            loadQuestion();
        }

        function loadQuestion() {
            const question = quizQuestions[currentQuestionIndex];
            questionText.textContent = question.question;
            optionsContainer.innerHTML = '';
            
            currentQuestion.textContent = currentQuestionIndex + 1;
            
            question.options.forEach((option, index) => {
                const optionBtn = document.createElement('button');
                optionBtn.className = 'option-btn';
                optionBtn.textContent = option;
                optionBtn.addEventListener('click', () => selectOption(index));
                optionsContainer.appendChild(optionBtn);
            });
            
            gameFeedback.textContent = '';
            nextQuestionBtn.style.display = 'none';
            finishGameBtn.style.display = 'none';
        }

        function selectOption(optionIndex) {
            if (selectedOption !== null) return;
            
            selectedOption = optionIndex;
            const question = quizQuestions[currentQuestionIndex];
            const optionBtns = document.querySelectorAll('.option-btn');
            
            optionBtns.forEach((btn, index) => {
                if (index === question.correct) {
                    btn.classList.add('correct');
                } else if (index === optionIndex && index !== question.correct) {
                    btn.classList.add('incorrect');
                }
                btn.disabled = true;
            });
            
            // Mostrar animación de feedback
            const isCorrect = optionIndex === question.correct;
            showFeedbackAnimation(isCorrect);
            
            if (isCorrect) {
                userScore++;
                updateScore();
                gameFeedback.textContent = `¡Correcto! ${question.explanation}`;
                gameFeedback.style.color = 'var(--success)';
            } else {
                gameFeedback.textContent = `Incorrecto. ${question.explanation}`;
                gameFeedback.style.color = 'var(--accent)';
            }
            
            if (currentQuestionIndex < quizQuestions.length - 1) {
                nextQuestionBtn.style.display = 'block';
            } else {
                finishGameBtn.style.display = 'block';
            }
        }

        function nextQuestion() {
            currentQuestionIndex++;
            selectedOption = null;
            loadQuestion();
        }

        function finishGame() {
            showResults();
        }

        function updateScore() {
            score.textContent = userScore;
        }

        function showResults() {
            const percentage = (userScore / quizQuestions.length) * 100;
            let message = '';
            let trophy = '🏆';
            
            if (percentage >= 90) {
                message = '¡Excelente! Eres un experto en lenguajes de programación.';
                trophy = '🏆';
            } else if (percentage >= 70) {
                message = '¡Muy bien! Tienes buenos conocimientos de programación.';
                trophy = '🥈';
            } else if (percentage >= 50) {
                message = 'Buen trabajo, pero aún hay espacio para mejorar.';
                trophy = '🥉';
            } else {
                message = 'Sigue estudiando, ¡puedes mejorar!';
                trophy = '📚';
            }
            
            resultsContainer.innerHTML = `
                <div class="trophy">${trophy}</div>
                <div class="score-display">${userScore}/${quizQuestions.length}</div>
                <div class="results-message">${message}</div>
                <button class="btn" id="playAgainBtn">Jugar de Nuevo</button>
            `;
            
            resultsModal.style.display = 'block';
            
            document.getElementById('playAgainBtn').addEventListener('click', () => {
                resultsModal.style.display = 'none';
                startGame();
            });
        }

        // Función para mostrar/ocultar la sección Acerca de
        function toggleAboutSection() {
            if (aboutContent.style.display === 'block') {
                aboutContent.style.display = 'none';
            } else {
                aboutContent.style.display = 'block';
            }
        }

        // Funciones para el chatbot
        function toggleChatbot() {
            if (chatbotContent.style.display === 'flex') {
                chatbotContent.style.display = 'none';
            } else {
                chatbotContent.style.display = 'flex';
                // Enfocar el input cuando se abre el chat
                setTimeout(() => {
                    chatbotInput.focus();
                }, 100);
            }
        }

        function addMessage(message, isUser = false) {
            const messageElement = document.createElement('div');
            messageElement.className = `message ${isUser ? 'user-message' : 'bot-message'}`;
            messageElement.textContent = message;
            chatbotMessages.appendChild(messageElement);
            chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
        }

        function getBotResponse(userMessage) {
            const lowerMessage = userMessage.toLowerCase();
            
            // Buscar coincidencias en la base de conocimientos
            for (const [key, responses] of Object.entries(chatbotKnowledge)) {
                if (lowerMessage.includes(key)) {
                    return responses[Math.floor(Math.random() * responses.length)];
                }
            }
            
            // Si no encuentra coincidencia, buscar por nombre de lenguaje
            for (const language of languages) {
                if (lowerMessage.includes(language.name.toLowerCase())) {
                    return `Sobre ${language.name}: ${language.description}`;
                }
            }
            
            // Respuesta por defecto
            const defaultResponses = [
                "No estoy seguro de entender tu pregunta. ¿Podrías reformularla?",
                "No tengo información sobre eso. ¿Podrías preguntarme sobre algún lenguaje de programación específico?",
                "Lo siento, no puedo responder a eso. ¿Te interesa saber sobre algún lenguaje de programación en particular?",
                "No conozco la respuesta a esa pregunta. ¿Quieres saber sobre las características de algún lenguaje?"
            ];
            
            return defaultResponses[Math.floor(Math.random() * defaultResponses.length)];
        }

        function sendMessage() {
            const message = chatbotInput.value.trim();
            if (message === '') return;
            
            // Añadir mensaje del usuario
            addMessage(message, true);
            chatbotInput.value = '';
            
            // Mostrar indicador de escritura
            typingIndicator.style.display = 'block';
            chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
            
            // Simular tiempo de respuesta
            setTimeout(() => {
                typingIndicator.style.display = 'none';
                const botResponse = getBotResponse(message);
                addMessage(botResponse, false);
            }, 1000 + Math.random() * 1000);
        }

        // Event listeners
        searchInput.addEventListener('input', searchLanguages);
        
        // Cerrar modal al hacer clic en la X
        closeModal.addEventListener('click', function() {
            languageModal.style.display = 'none';
        });
        
        // Cerrar modal al hacer clic fuera del contenido
        languageModal.addEventListener('click', function(event) {
            if (event.target === languageModal) {
                languageModal.style.display = 'none';
            }
        });
        
        // Cerrar modal con la tecla Escape
        document.addEventListener('keydown', function(event) {
            if (event.key === 'Escape') {
                languageModal.style.display = 'none';
                resultsModal.style.display = 'none';
            }
        });

        // Event listeners del juego
        startGameBtn.addEventListener('click', startGame);
        nextQuestionBtn.addEventListener('click', nextQuestion);
        finishGameBtn.addEventListener('click', finishGame);
        closeResultsModal.addEventListener('click', () => {
            resultsModal.style.display = 'none';
        });

        // Event listener para la sección Acerca de
        aboutBtn.addEventListener('click', toggleAboutSection);
        
        // Cerrar la sección Acerca de al hacer clic fuera de ella
        document.addEventListener('click', function(event) {
            if (!event.target.closest('.about-section') && aboutContent.style.display === 'block') {
                aboutContent.style.display = 'none';
            }
        });

        // Event listeners para el chatbot
        chatbotBtn.addEventListener('click', toggleChatbot);
        sendMessageBtn.addEventListener('click', sendMessage);
        chatbotInput.addEventListener('keypress', function(event) {
            if (event.key === 'Enter') {
                sendMessage();
            }
        });
        
        // Cerrar el chatbot al hacer clic fuera de él
        document.addEventListener('click', function(event) {
            if (!event.target.closest('.chatbot-section') && chatbotContent.style.display === 'flex') {
                chatbotContent.style.display = 'none';
            }
        });

        // Inicializar la página
        displayLanguages();
        
        // Inicializar la lluvia de logos
        window.addEventListener('load', createLogoRain);
    </script>
</body>
</html>
