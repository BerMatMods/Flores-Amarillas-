<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feliz Día de las Flores Amarillas</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Montserrat:wght@700&family=Roboto+Mono:wght@500&display=swap" rel="stylesheet">
    <style>
        *,
        *::after,
        *::before {
            padding: 0;
            margin: 0;
            box-sizing: border-box;
        }

        :root {
            --dark-color: #000;
            --fl-speed: 0.8s;
            --speed-leaf: 2s;
        }

        body {
            display: flex;
            align-items: flex-end;
            justify-content: center;
            min-height: 100vh;
            background-color: var(--dark-color);
            overflow: hidden;
            perspective: 1000px;
            font-family: 'Montserrat', sans-serif;
            cursor: none;
            position: relative;
        }

        /* === FONDO ORIGINAL RESTAURADO === */
        .night {
            position: fixed;
            left: 50%;
            top: 0;
            transform: translateX(-50%);
            width: 100%;
            height: 100%;
            filter: blur(0.1vmin);
            background-image: radial-gradient(
                    ellipse at top,
                    transparent 0%,
                    var(--dark-color)
                ),
                radial-gradient(
                    ellipse at bottom,
                    var(--dark-color),
                    rgba(145, 233, 255, 0.2)
                ),
                repeating-linear-gradient(
                    220deg,
                    rgb(0, 0, 0) 0px,
                    rgb(0, 0, 0) 19px,
                    transparent 19px,
                    transparent 22px
                ),
                repeating-linear-gradient(
                    189deg,
                    rgb(0, 0, 0) 0px,
                    rgb(0, 0, 0) 19px,
                    transparent 19px,
                    transparent 22px
                ),
                repeating-linear-gradient(
                    148deg,
                    rgb(0, 0, 0) 0px,
                    rgb(0, 0, 0) 19px,
                    transparent 19px,
                    transparent 22px
                ),
                linear-gradient(90deg, rgb(0, 255, 250), rgb(240, 240, 240));
        }

        .shooting-stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .shooting-star {
            position: absolute;
            width: 4px;
            height: 4px;
            background: #fff;
            border-radius: 50%;
            box-shadow: 0 0 6px 2px rgba(255, 255, 255, 0.8);
            opacity: 0;
            animation: shootingStar 3s linear infinite;
        }

        .shooting-star::before {
            content: '';
            position: absolute;
            top: 50%;
            right: 0;
            transform: translateY(-50%);
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
            animation: shootingStarTail 3s linear infinite;
        }

        @keyframes shootingStar {
            0% { opacity: 0; transform: translateX(0) translateY(0) rotate(45deg); }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { opacity: 0; transform: translateX(120vw) translateY(50vh) rotate(10deg); }
        }

        @keyframes shootingStarTail {
            0% { width: 0; }
            30% { width: 100px; }
            100% { width: 0; }
        }

        /* === Lluvia de palabras doradas con cuadritos neón (Matrix Style) === */
        .love-rain {
            position: fixed;
            top: -20px;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .love-word-container {
            position: absolute;
            top: -60px;
            opacity: 0;
            animation: fallContainer 12s linear infinite;
        }

        .love-word {
            display: inline-block;
            background: rgba(255, 215, 0, 0.15);
            border: 1px solid rgba(255, 215, 0, 0.6);
            color: #ffd700;
            font-family: 'Roboto Mono', monospace;
            font-size: 1.8vmin;
            font-weight: 700;
            padding: 4px 8px;
            border-radius: 6px;
            box-shadow: 0 0 10px rgba(255, 215, 0, 0.7),
                        0 0 20px rgba(255, 215, 0, 0.4);
            text-shadow: 0 0 5px #ffd700;
            white-space: nowrap;
        }

        @keyframes fallContainer {
            0% { transform: translateY(-100vh); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(110vh); opacity: 0; }
        }

        /* === Lluvia de corazones y girasoles flotando === */
        .floating-items {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .floating-item {
            position: absolute;
            font-size: 2.5vmin;
            opacity: 0.9;
            animation: floatUp 20s linear infinite;
        }

        @keyframes floatUp {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 0.3; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-20vh) rotate(360deg); opacity: 0; }
        }

        /* === FLORES ORIGINALES SIN MODIFICAR === */
        .flowers {
            position: relative;
            transform: scale(0.7);
            z-index: 2;
        }

        .flower {
            position: absolute;
            bottom: 15vmin;
            transform-origin: bottom center;
            z-index: 50;
        }

        /* Animaciones originales intactas */
        .flower--1 { animation: moving-flower-1 4s linear infinite; }
        .flower--1 .flower__line { height: 70vmin; animation-delay: 0.3s; }
        .flower--1 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 1.6s backwards; }
        .flower--1 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 1.4s backwards; }
        .flower--1 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 1.2s backwards; }
        .flower--1 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 1s backwards; }

        .flower--2 {
            left: 50%;
            transform: rotate(20deg);
            animation: moving-flower-2 4s linear infinite;
        }
        .flower--2 .flower__line { height: 60vmin; animation-delay: 0.6s; }
        .flower--2 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 1.9s backwards; }
        .flower--2 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 1.7s backwards; }
        .flower--2 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 1.5s backwards; }
        .flower--2 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 1.3s backwards; }

        .flower--3 {
            left: 50%;
            transform: rotate(-15deg);
            animation: moving-flower-3 4s linear infinite;
        }
        .flower--3 .flower__line { animation-delay: 0.9s; }
        .flower--3 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 2.5s backwards; }
        .flower--3 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 2.3s backwards; }
        .flower--3 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 2.1s backwards; }
        .flower--3 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 1.9s backwards; }

        .flower--4 {
            left: -25%;
            z-index: -6;
            transform: rotate(10deg);
            animation: moving-flower-4 3.5s linear infinite;
        }
        .flower--4 .flower__line { height: 90vmin; animation-delay: 1.2s; }
        .flower--4 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 2.8s backwards; }
        .flower--4 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 2.6s backwards; }
        .flower--4 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 2.4s backwards; }
        .flower--4 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 2.2s backwards; }

        .flower--5 {
            left: 75%;
            z-index: -7;
            transform: rotate(-25deg);
            animation: moving-flower-5 4.5s linear infinite;
        }
        .flower--5 .flower__line { height: 85vmin; animation-delay: 1.9s; }
        .flower--5 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 2.7s backwards; }
        .flower--5 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 2.5s backwards; }
        .flower--5 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 2.3s backwards; }
        .flower--5 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 2.1s backwards; }

        /* === RESTO DEL CÓDIGO ORIGINAL SIN TOCAR === */
        .flower__leafs {
            position: relative;
            animation: blooming-flower 2s backwards;
        }

        .flower__leafs--1 { animation-delay: 1.1s; }
        .flower__leafs--2 { animation-delay: 1.4s; }
        .flower__leafs--3 { animation-delay: 1.7s; }
        .flower__leafs--4 { animation-delay: 2.0s; }
        .flower__leafs--5 { animation-delay: 2.0s; }

        .flower__leafs::after {
            content: "";
            position: absolute;
            left: 0;
            top: 0;
            transform: translate(-50%, -100%);
            width: 8vmin;
            height: 8vmin;
            background-color: #6bf0ff;
            filter: blur(10vmin);
        }

        .flower__leaf {
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 23vmin;
            height: 6vmin;
            border-radius: 60% 40% 60% 40%;
            background-color: #ffd700;
            background-image: linear-gradient(to top, #ff8c00, #ffd700, #ffff00);
            transform-origin: bottom center;
            opacity: 0.95;
            box-shadow: inset 0 0 1vmin rgba(255, 255, 255, 0.7), 0 0 3vmin rgba(255, 215, 0, 0.4);
            z-index: 2;
        }

        .flower__leaf--1 { transform: translate(-50%, -10%) rotate(-45deg); }
        .flower__leaf--2 { transform: translate(-50%, -10%) rotate(-15deg); }
        .flower__leaf--3 { transform: translate(-50%, -10%) rotate(15deg); }
        .flower__leaf--4 { transform: translate(-50%, -10%) rotate(45deg); }

        .flower__white-circle {
            position: absolute;
            left: -4vmin;
            top: -4vmin;
            width: 10vmin;
            height: 10vmin;
            border-radius: 50%;
            background-color: #8b4513;
            background-image: radial-gradient(circle at 30% 30%, #654321, #8b4513, #2f1b14);
            box-shadow: inset 0 0 2vmin rgba(0, 0, 0, 0.8),
                        0 0 1vmin rgba(139, 69, 19, 0.6);
        }

        .flower__white-circle::after {
            content: "";
            position: absolute;
            left: 46%;
            top: 31%;
            transform: translate(-50%, -50%);
            width: 80%;
            height: 80%;
            z-index: 3;
            border-radius: inherit;
            background-image: repeating-conic-gradient(
                from 0deg,
                #2f1b14 0deg 15deg,
                #654321 15deg 30deg
            ), radial-gradient(circle at center, #8b4513, #654321);
        }

        .flower__line {
            height: 55vmin;
            width: 2vmin;
            background-image: linear-gradient(
                to left,
                rgb(0, 0, 0, 0.3),
                transparent,
                rgba(255, 255, 255, 0.2)
            ), linear-gradient(to top, transparent 10%, #2d5016, #4a7c23, #6b8e23);
            box-shadow: inset 0 0 2px rgba(0, 0, 0, 0.7);
            animation: grow-flower-tree 4s backwards;
        }

        .flower__line__leaf {
            --w: 8vmin;
            --h: calc(var(--w) + 3vmin);
            position: absolute;
            top: 20%;
            left: 90%;
            width: var(--w);
            height: var(--h);
            border-top-right-radius: var(--h);
            border-bottom-left-radius: var(--h);
            background-image: linear-gradient(
                to top,
                rgba(45, 80, 22, 0.6),
                #4a7c23,
                #6b8e23
            );
            box-shadow: inset 0 0 1vmin rgba(0, 0, 0, 0.3);
        }

        .flower__line__leaf--1 { transform: rotate(70deg) rotateY(30deg); }
        .flower__line__leaf--2 { top: 45%; transform: rotate(70deg) rotateY(30deg); }
        .flower__line__leaf--3,
        .flower__line__leaf--4 {
            border-top-right-radius: 0;
            border-bottom-left-radius: 0;
            border-top-left-radius: var(--h);
            border-bottom-right-radius: var(--h);
            left: -460%;
            top: 12%;
            transform: rotate(-70deg) rotateY(30deg);
        }
        .flower__line__leaf--4 { top: 40%; }

        .flower__light {
            position: absolute;
            bottom: 0vmin;
            width: 0.8vmin;
            height: 0.8vmin;
            background-color: #8b4513;
            border-radius: 50%;
            filter: blur(0.1vmin);
            animation: sunflower-seeds 6s linear infinite backwards;
            box-shadow: 0 0 1vmin rgba(139, 69, 19, 0.8);
        }

        .flower__light:nth-child(odd) { background-color: #654321; }
        .flower__light--1 { left: -2vmin; animation-delay: 1s; }
        .flower__light--2 { left: 3vmin; animation-delay: 0.5s; }
        .flower__light--3 { left: -6vmin; animation-delay: 0.3s; }
        .flower__light--4 { left: 6vmin; animation-delay: 0.9s; }
        .flower__light--5 { left: -1vmin; animation-delay: 1.5s; }
        .flower__light--6 { left: -4vmin; animation-delay: 3s; }
        .flower__light--7 { left: 3vmin; animation-delay: 2s; }
        .flower__light--8 { left: -6vmin; animation-delay: 3.5s; }

        /* === HIERBAS Y ANIMACIONES ORIGINALES === */
        .flower__grass {
            --c: #4a7c23;
            --line-w: 2vmin;
            position: absolute;
            bottom: 12vmin;
            left: -7vmin;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            z-index: 20;
            transform-origin: bottom center;
            transform: rotate(-48deg) rotateY(40deg);
        }

        .flower__grass--1 { animation: moving-grass 2s linear infinite; }
        .flower__grass--2 {
            left: 2vmin;
            bottom: 10vmin;
            transform: scale(0.5) rotate(75deg) rotateX(10deg) rotateY(-200deg);
            opacity: 0.8;
            z-index: 0;
            animation: moving-grass--2 1.5s linear infinite;
        }

        /* === KEYFRAMES ORIGINALES === */
        @keyframes moving-flower-1 { 0%, 100% { transform: rotate(2deg); } 50% { transform: rotate(-2deg); } }
        @keyframes moving-flower-2 { 0%, 100% { transform: rotate(18deg); } 50% { transform: rotate(14deg); } }
        @keyframes moving-flower-3 { 0%, 100% { transform: rotate(-18deg); } 50% { transform: rotate(-20deg) rotateY(-10deg); } }
        @keyframes moving-flower-4 { 0%, 100% { transform: rotate(9deg); } 50% { transform: rotate(12deg) rotateY(9deg); } }
        @keyframes moving-flower-5 { 0%, 100% { transform: rotate(-5deg); } 50% { transform: rotate(-11deg) rotateY(5deg); } }

        @keyframes blooming-leaf-right { 0% { transform-origin: left; transform: rotate(70deg) rotateY(30deg) scale(0); } }
        @keyframes blooming-leaf-left { 0% { transform-origin: right; transform: rotate(-70deg) rotateY(30deg) scale(0); } }
        @keyframes grow-flower-tree { 0% { height: 0; border-radius: 1vmin; } }
        @keyframes blooming-flower { 0% { transform: scale(0); } }

        /* === CARTA VERTICAL - MÁS ARRIBA, COMPACTA, FUENTE GRUESA === */
        .vertical-card {
            position: fixed;
            top: 8%; /* Más arriba */
            left: 50%;
            transform: translateX(-50%);
            width: 80%;
            max-width: 400px;
            background: rgba(255, 255, 220, 0.9);
            border-radius: 18px;
            padding: 20px 18px;
            box-shadow: 0 0 25px rgba(255, 215, 0, 0.7);
            border: 2px solid #ffd700;
            z-index: 1000;
            font-family: 'Montserrat', sans-serif;
            color: #333;
            text-align: center;
            font-size: 1.8vmin;
            line-height: 1.5;
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            opacity: 0;
            animation: slideInVertical 2.5s 1s forwards;
        }

        .vertical-card h2 {
            font-family: 'Dancing Script', cursive;
            font-size: 2.6vmin;
            color: #d4af37;
            margin-bottom: 15px;
            text-shadow: 0 0 4px rgba(255, 215, 0, 0.5);
            font-weight: 600;
        }

        .vertical-card p {
            margin: 8px 0;
            font-size: 1.8vmin;
            font-weight: 700;
            color: #333;
            line-height: 1.4;
        }

        .vertical-card .emoji {
            font-size: 2vmin;
            margin: 0 3px;
        }

        @keyframes slideInVertical {
            0% { opacity: 0; transform: translateX(-50%) translateY(-30px); }
            100% { opacity: 1; transform: translateX(-50%) translateY(0); }
        }

        /* === MENÚ DE 3 RAYAS === */
        .menu-btn {
            position: fixed;
            top: 20px;
            left: 20px;
            width: 50px;
            height: 50px;
            background: rgba(255, 215, 0, 0.9);
            border-radius: 12px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 2000;
            box-shadow: 0 0 12px rgba(255, 255, 255, 0.7);
            transition: transform 0.3s;
        }

        .menu-btn:hover { transform: scale(1.1); }

        .menu-btn span {
            display: block;
            width: 70%;
            height: 3.5px;
            background: #000;
            margin: 4px 0;
            transition: 0.3s;
            border-radius: 2px;
        }

        .menu-open .menu-btn span:nth-child(1) { transform: rotate(45deg) translate(5px, 5px); }
        .menu-open .menu-btn span:nth-child(2) { opacity: 0; }
        .menu-open .menu-btn span:nth-child(3) { transform: rotate(-45deg) translate(5px, -5px); }

        .menu-panel {
            position: fixed;
            top: 0;
            left: -320px;
            width: 300px;
            height: 100%;
            background: rgba(0, 0, 0, 0.95);
            color: #fff;
            padding: 70px 20px 20px;
            transition: left 0.5s ease;
            z-index: 1999;
            font-family: 'Montserrat', sans-serif;
            overflow-y: auto;
            border-right: 2px solid #ffd700;
        }

        .menu-open .menu-panel { left: 0; }

        .menu-panel h3 { color: #ffd700; margin-bottom: 15px; }
        .menu-panel p, .menu-panel a { margin: 12px 0; }
        .menu-panel a { color: #ffd700; text-decoration: underline; }
        /* === ABEJAS VOLANDO === */
        .bee {
            position: fixed;
            font-size: 2.8vmin;
            z-index: 5;
            animation: fly 12s infinite linear;
            opacity: 0.95;
            pointer-events: none;
        }

        @keyframes fly {
            0% { transform: translate(0, 0) rotate(0deg); }
            25% { transform: translate(25vw, 12vh) rotate(45deg); }
            50% { transform: translate(50vw, 8vh) rotate(90deg); }
            75% { transform: translate(75vw, 15vh) rotate(135deg); }
            100% { transform: translate(0, 0) rotate(180deg); }
        }

        /* === EXPLOSIÓN DE GIRASOLES (PERFECTA) === */
        .explosion {
            position: absolute;
            pointer-events: none;
            z-index: 9999;
        }

        .explosion .emoji {
            position: absolute;
            font-size: 1.4vmin;
            color: #ffd700;
            opacity: 1;
            animation: explode 1.4s cubic-bezier(0.2, 0.8, 0.8, 0.2) forwards;
            text-shadow: 0 0 3px rgba(0,0,0,0.3);
        }

        @keyframes explode {
            0% { transform: scale(0) rotate(0deg); opacity: 0; }
            10% { opacity: 1; transform: scale(0.8); }
            100% { transform: translate(var(--x), var(--y)) scale(4.5) rotate(360deg); opacity: 0; }
        }

        /* === CRÉDITOS EN LA PARTE INFERIOR === */
        .credits {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            color: #fff;
            font-family: 'Montserrat', sans-serif;
            font-size: 1.6vmin;
            font-weight: 600;
            text-shadow: 0 0 5px rgba(0,0,0,0.8);
            z-index: 1000;
            background: rgba(0, 0, 0, 0.6);
            padding: 10px 20px;
            border-radius: 10px;
            border: 1px solid #ffd700;
        }
    </style>
</head>
<body class="not-loaded">
    <div class="night"></div>
    <div class="shooting-stars"></div>

    <!-- === Lluvia de palabras doradas con emojis (Matrix Style) === -->
    <div class="love-rain" id="loveRain"></div>

    <!-- === Lluvia de corazones y girasoles flotando === -->
    <div class="floating-items" id="floatingItems"></div>

    <!-- === CARTA VERTICAL - TEXTO QUE SE ESCRIBE AUTOMÁTICAMENTE === -->
    <div class="vertical-card" id="verticalCard">
        <h2 id="title"></h2>
        <div id="content"></div>
    </div>

    <!-- === MENÚ DE 3 RAYAS === -->
    <div class="menu-btn" id="menuBtn">
        <span></span>
        <span></span>
        <span></span>
    </div>

    <div class="menu-panel" id="menuPanel">
        <h3>Menú - AnthZz Berrocal</h3>
        <p>Desarrollador web | 🧑‍💻👑| BerMatMods</p>
        <p>Diseño experiencias únicas con amor y código 💻✨</p>
        <a href="https://wa.me/51930569195" target="_blank">💬 Escríbeme en WhatsApp</a>
        <p>Proyectos: Detalles virtuales, interfaces mágicas, cartas interactivas. ETC...</p>
        <p>Créditos: By AnthZz Berrocal BerMatMods © 2025</p>
    </div>

    <!-- === FLORES ORIGINALES SIN MODIFICAR === -->
    <div class="flowers">
        <!-- Flor 1 -->
        <div class="flower flower--1">
            <div class="flower__leafs flower__leafs--1">
                <div class="flower__leaf flower__leaf--1"></div>
                <div class="flower__leaf flower__leaf--2"></div>
                <div class="flower__leaf flower__leaf--3"></div>
                <div class="flower__leaf flower__leaf--4"></div>
                <div class="flower__white-circle"></div>
                <div class="flower__light flower__light--1"></div>
                <div class="flower__light flower__light--2"></div>
                <div class="flower__light flower__light--3"></div>
                <div class="flower__light flower__light--4"></div>
                <div class="flower__light flower__light--5"></div>
                <div class="flower__light flower__light--6"></div>
                <div class="flower__light flower__light--7"></div>
                <div class="flower__light flower__light--8"></div>
            </div>
            <div class="flower__line">
                <div class="flower__line__leaf flower__line__leaf--1"></div>
                <div class="flower__line__leaf flower__line__leaf--2"></div>
                <div class="flower__line__leaf flower__line__leaf--3"></div>
                <div class="flower__line__leaf flower__line__leaf--4"></div>
            </div>
        </div>

        <!-- Flor 2 -->
        <div class="flower flower--2">
            <div class="flower__leafs flower__leafs--2">
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
                <div class="flower__white-circle"></div>
                <div class="flower__light flower__light--1"></div>
                <div class="flower__light flower__light--2"></div>
                <div class="flower__light flower__light--3"></div>
                <div class="flower__light flower__light--4"></div>
                <div class="flower__light flower__light--5"></div>
                <div class="flower__light flower__light--6"></div>
                <div class="flower__light flower__light--7"></div>
                <div class="flower__light flower__light--8"></div>
            </div>
            <div class="flower__line">
                <div class="flower__line__leaf flower__line__leaf--1"></div>
                <div class="flower__line__leaf flower__line__leaf--2"></div>
                <div class="flower__line__leaf flower__line__leaf--3"></div>
                <div class="flower__line__leaf flower__line__leaf--4"></div>
            </div>
        </div>

        <!-- Flor 3 -->
        <div class="flower flower--3">
            <div class="flower__leafs flower__leafs--3">
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
                <div class="flower__white-circle"></div>
                <div class="flower__light flower__light--1"></div>
                <div class="flower__light flower__light--2"></div>
                <div class="flower__light flower__light--3"></div>
                <div class="flower__light flower__light--4"></div>
                <div class="flower__light flower__light--5"></div>
                <div class="flower__light flower__light--6"></div>
                <div class="flower__light flower__light--7"></div>
                <div class="flower__light flower__light--8"></div>
            </div>
            <div class="flower__line">
                <div class="flower__line__leaf flower__line__leaf--1"></div>
                <div class="flower__line__leaf flower__line__leaf--2"></div>
                <div class="flower__line__leaf flower__line__leaf--3"></div>
                <div class="flower__line__leaf flower__line__leaf--4"></div>
            </div>
        </div>

        <!-- Flor 4 -->
        <div class="flower flower--4">
            <div class="flower__leafs flower__leafs--4">
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
                <div class="flower__white-circle"></div>
                <div class="flower__light flower__light--1"></div>
                <div class="flower__light flower__light--2"></div>
                <div class="flower__light flower__light--3"></div>
                <div class="flower__light flower__light--4"></div>
                <div class="flower__light flower__light--5"></div>
                <div class="flower__light flower__light--6"></div>
                <div class="flower__light flower__light--7"></div>
                <div class="flower__light flower__light--8"></div>
            </div>
            <div class="flower__line">
                <div class="flower__line__leaf flower__line__leaf--1"></div>
                <div class="flower__line__leaf flower__line__leaf--2"></div>
                <div class="flower__line__leaf flower__line__leaf--3"></div>
                <div class="flower__line__leaf flower__line__leaf--4"></div>
            </div>
        </div>

        <!-- Flor 5 -->
        <div class="flower flower--5">
            <div class="flower__leafs flower__leafs--5">
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
                <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
                <div class="flower__white-circle"></div>
                <div class="flower__light flower__light--1"></div>
                <div class="flower__light flower__light--2"></div>
                <div class="flower__light flower__light--3"></div>
                <div class="flower__light flower__light--4"></div>
                <div class="flower__light flower__light--5"></div>
                <div class="flower__light flower__light--6"></div>
                <div class="flower__light flower__light--7"></div>
                <div class="flower__light flower__light--8"></div>
            </div>
            <div class="flower__line">
                <div class="flower__line__leaf flower__line__leaf--1"></div>
                <div class="flower__line__leaf flower__line__leaf--2"></div>
                <div class="flower__line__leaf flower__line__leaf--3"></div>
                <div class="flower__line__leaf flower__line__leaf--4"></div>
            </div>
        </div>

        <!-- Hierbas -->
        <div class="grow-ans" style="--d:1.2s">
            <div class="flower__g-long">
                <div class="flower__g-long__top"></div>
                <div class="flower__g-long__bottom"></div>
            </div>
        </div>

        <div class="growing-grass">
            <div class="flower__grass flower__grass--1">
                <div class="flower__grass--top"></div>
                <div class="flower__grass--bottom"></div>
                <div class="flower__grass__leaf flower__grass__leaf--1"></div>
                <div class="flower__grass__leaf flower__grass__leaf--2"></div>
                <div class="flower__grass__leaf flower__grass__leaf--3"></div>
                <div class="flower__grass__leaf flower__grass__leaf--4"></div>
                <div class="flower__grass__leaf flower__grass__leaf--5"></div>
                <div class="flower__grass__leaf flower__grass__leaf--6"></div>
                <div class="flower__grass__leaf flower__grass__leaf--7"></div>
                <div class="flower__grass__leaf flower__grass__leaf--8"></div>
                <div class="flower__grass__overlay"></div>
            </div>
        </div>
    </div>

    <!-- === CRÉDITOS === -->
    <div class="credits">By AnthZz Berrocal BerMatMods</div>

    <script>
        // === ESCRITURA AUTOMÁTICA DE LA CARTA CON ✍️ ===
        window.onload = () => {
            setTimeout(() => {
                document.body.classList.remove("not-loaded");
            }, 1000);

            const titleElement = document.getElementById('title');
            const contentElement = document.getElementById('content');
            const titleText = "Feliz Día de las Flores Amarillas 🌻💛";
            const contentText = [
                "Para ti mi Amor, que iluminas cada día como el sol 🌞",
                "🌻",
                "Tus sonrisas son como girasoles en primavera 🌸",
                "🐝💛",
                "Que esta noche estrellada te traiga paz, amor y alegría 💫",
                "✨🌻✨",
                "Siempre estaré aquí, siguiéndote como el girasol sigue al sol 🌻→☀️",
                "Cada latido mío canta tu nombre 🎶",
                "Eres mi milagro diario, mi razón de sonreír 😊",
                "Gracias por existir, por brillar, por ser tú 💖",
                "Como los girasoles, mi amor por ti nunca se apaga 🌻→❤️",
                "Donde quiera que vayas, te sigo con el alma 🌍💫",
                "Porque tú eres mi luz, mi calor, mi todo 💛",
                "Y en cada pétalo, hay una palabra de amor para ti 💌",
                "Con todo mi corazón...<br>Te Amo muchísimo mi reina 💛"
            ];

            let charIndex = 0;
            let pIndex = 0;
            const speed = 40; // Velocidad de escritura (ms por caracter)

            function typeTitle() {
                if (charIndex < titleText.length) {
                    titleElement.textContent += titleText.charAt(charIndex);
                    charIndex++;
                    setTimeout(typeTitle, speed);
                } else {
                    setTimeout(typeContent, 500);
                }
            }

            function typeContent() {
                if (pIndex < contentText.length) {
                    const p = document.createElement('p');
                    p.innerHTML = '✍️ '; // Emoji de lápiz al inicio
                    contentElement.appendChild(p);

                    let textIndex = 0;
                    const currentText = contentText[pIndex];

                    function typeChar() {
                        if (textIndex < currentText.length) {
                            p.innerHTML = '✍️ ' + currentText.substring(0, textIndex + 1);
                            textIndex++;
                            setTimeout(typeChar, speed);
                        } else {
                            pIndex++;
                            setTimeout(typeContent, 400);
                        }
                    }
                    setTimeout(typeChar, 200);
                }
            }

            typeTitle();
        };

        // === Lluvia de palabras doradas con emojis (Matrix Style) ===
        const loveMessages = [
            'Te amo 💖', 'Eres hermosa 🌸', 'Mi corazón es tuyo 💓', 'Brillas como el sol ☀️',
            'Eres mi todo 💛', 'Te admiro profundamente 🌻', 'Eres única en el mundo 🌍',
            'Gracias por existir 🙏', 'Eres mi milagro diario ✨', 'Floreciste en mí 🌱',
            'Eres luz en mi oscuridad 💡', 'Mi alma te reconoce 🕊️', 'Eres mi paz interior 🕉️',
            'Te extraño cada segundo ⏳', 'Eres mi razón de sonreír 😊', 'Eres mi cielo 🌌',
            'Te pienso todo el día 🧠', 'Eres mi refugio 🏡', 'Eres perfecta tal como eres 🌟',
            'Mi amor por ti crece 🌿', 'Eres mi musa artística 🎨', 'Eres mi fuerza 💪',
            'Contigo todo tiene sentido 🧩', 'Eres mi eternidad ∞', 'Te cuido con el alma 🛡️',
            'Eres mi sueño hecho realidad 💤', 'Eres mi reina 👑', 'Te protejo con fuego 🔥',
            'Eres mi melodía 🎵', 'Mi vida contigo es arte 🖼️'
        ];

        const loveRain = document.getElementById('loveRain');

        function createWord() {
            const container = document.createElement('div');
            container.className = 'love-word-container';
            container.style.left = Math.random() * 100 + 'vw';
            container.style.animationDuration = (Math.random() * 6 + 10) + 's';

            const word = document.createElement('div');
            word.className = 'love-word';
            word.textContent = loveMessages[Math.floor(Math.random() * loveMessages.length)];

            container.appendChild(word);
            loveRain.appendChild(container);

            setTimeout(() => container.remove(), 12000);
        }

        setInterval(createWord, 400);
        // === Lluvia de corazones y girasoles flotando ===
        const floatingItems = document.getElementById('floatingItems');
        const items = ['💖', '💗', '💓', '💞', '💘', '💝', '🌻', '🌼'];
        setInterval(() => {
            const item = document.createElement('div');
            item.className = 'floating-item';
            item.textContent = items[Math.floor(Math.random() * items.length)];
            item.style.left = Math.random() * 100 + 'vw';
            item.style.animationDuration = (Math.random() * 15 + 10) + 's';
            floatingItems.appendChild(item);
            setTimeout(() => item.remove(), 25000);
        }, 600);

        // === EXPLOSIÓN DE GIRASOLES (PERFECTA) ===
        document.addEventListener('click', (e) => {
            const explosion = document.createElement('div');
            explosion.className = 'explosion';
            explosion.style.left = e.clientX + 'px';
            explosion.style.top = e.clientY + 'px';

            for (let i = 0; i < 75; i++) {
                const emoji = document.createElement('div');
                emoji.className = 'emoji';
                emoji.textContent = '🌻';
                const angle = Math.random() * 360;
                const distance = Math.random() * 200 + 120;
                emoji.style.setProperty('--x', Math.cos(angle * Math.PI / 180) * distance + 'px');
                emoji.style.setProperty('--y', Math.sin(angle * Math.PI / 180) * distance + 'px');
                explosion.appendChild(emoji);
            }

            document.body.appendChild(explosion);

            setTimeout(() => {
                explosion.remove();
            }, 1400);
        });

        // === ABEJAS VOLANDO ===
        for (let i = 0; i < 8; i++) {
            const bee = document.createElement('div');
            bee.className = 'bee';
            bee.textContent = '🐝';
            bee.style.left = Math.random() * 100 + 'vw';
            bee.style.top = Math.random() * 80 + 'vh';
            bee.style.animationDuration = (Math.random() * 8 + 8) + 's';
            bee.style.animationDelay = (Math.random() * 5) + 's';
            document.body.appendChild(bee);
        }

        // === MENÚ DE 3 RAYAS ===
        const menuBtn = document.getElementById('menuBtn');
        const menuPanel = document.getElementById('menuPanel');
        menuBtn.addEventListener('click', () => {
            document.body.classList.toggle('menu-open');
        });

        // === SHOOTING STARS ===
        function createStar() {
            const star = document.createElement('div');
            star.className = 'shooting-star';
            star.style.top = Math.random() * 60 + '%';
            star.style.animationDuration = (Math.random() * 1.5 + 2) + 's';
            document.querySelector('.shooting-stars').appendChild(star);
            setTimeout(() => star.remove(), 4000);
        }
        setInterval(() => {
            if (Math.random() > 0.3) createStar();
        }, 3000);
    </script>
</body>
</html>
