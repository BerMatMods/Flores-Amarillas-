
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

        /* === FLORES NUEVAS (ESTILO COMPLETO REEMPLAZADO) === */
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
        .flower--1 {
          animation: moving-flower-1 4s linear infinite;
        }
        .flower--1 .flower__line {
          height: 70vmin;
          animation-delay: 0.3s;
        }
        .flower--1 .flower__line__leaf--1 {
          animation: blooming-leaf-right var(--fl-speed) 1.6s backwards;
        }
        .flower--1 .flower__line__leaf--2 {
          animation: blooming-leaf-right var(--fl-speed) 1.4s backwards;
        }
        .flower--1 .flower__line__leaf--3 {
          animation: blooming-leaf-left var(--fl-speed) 1.2s backwards;
        }
        .flower--1 .flower__line__leaf--4 {
          animation: blooming-leaf-left var(--fl-speed) 1s backwards;
        }
        .flower--2 {
          left: 50%;
          transform: rotate(20deg);
          animation: moving-flower-2 4s linear infinite;
        }
        .flower--2 .flower__line {
          height: 60vmin;
          animation-delay: 0.6s;
        }
        .flower--2 .flower__line__leaf--1 {
          animation: blooming-leaf-right var(--fl-speed) 1.9s backwards;
        }
        .flower--2 .flower__line__leaf--2 {
          animation: blooming-leaf-right var(--fl-speed) 1.7s backwards;
        }
        .flower--2 .flower__line__leaf--3 {
          animation: blooming-leaf-left var(--fl-speed) 1.5s backwards;
        }
        .flower--2 .flower__line__leaf--4 {
          animation: blooming-leaf-left var(--fl-speed) 1.3s backwards;
        }
        .flower--3 {
          left: 50%;
          transform: rotate(-15deg);
          animation: moving-flower-3 4s linear infinite;
        }
        .flower--3 .flower__line {
          animation-delay: 0.9s;
        }
        .flower--3 .flower__line__leaf--1 {
          animation: blooming-leaf-right var(--fl-speed) 2.5s backwards;
        }
        .flower--3 .flower__line__leaf--2 {
          animation: blooming-leaf-right var(--fl-speed) 2.3s backwards;
        }
        .flower--3 .flower__line__leaf--3 {
          animation: blooming-leaf-left var(--fl-speed) 2.1s backwards;
        }
        .flower--3 .flower__line__leaf--4 {
          animation: blooming-leaf-left var(--fl-speed) 1.9s backwards;
        }
        .flower--4 {
          left: -25%;
          z-index: -6;
          transform: rotate(10deg);
          animation: moving-flower-4 3.5s linear infinite;
        }
        .flower--4 .flower__line {
          height: 90vmin;
          animation-delay: 1.2s;
        }
        .flower--4 .flower__line__leaf--1 {
          animation: blooming-leaf-right var(--fl-speed) 2.8s backwards;
        }
        .flower--4 .flower__line__leaf--2 {
          animation: blooming-leaf-right var(--fl-speed) 2.6s backwards;
        }
        .flower--4 .flower__line__leaf--3 {
          animation: blooming-leaf-left var(--fl-speed) 2.4s backwards;
        }
        .flower--4 .flower__line__leaf--4 {
          animation: blooming-leaf-left var(--fl-speed) 2.2s backwards;
        }
        .flower--5 {
          left: 75%;
          z-index: -7;
          transform: rotate(-25deg);
          animation: moving-flower-5 4.5s linear infinite;
        }
        .flower--5 .flower__line {
          height: 85vmin;
          animation-delay: 1.9s;
        }
        .flower--5 .flower__line__leaf--1 {
          animation: blooming-leaf-right var(--fl-speed) 2.7s backwards;
        }
        .flower--5 .flower__line__leaf--2 {
          animation: blooming-leaf-right var(--fl-speed) 2.5s backwards;
        }
        .flower--5 .flower__line__leaf--3 {
          animation: blooming-leaf-left var(--fl-speed) 2.3s backwards;
        }
        .flower--5 .flower__line__leaf--4 {
          animation: blooming-leaf-left var(--fl-speed) 2.1s backwards;
        }
        .flower__leafs {
          position: relative;
          animation: blooming-flower 2s backwards;
        }
        .flower__leafs--1 {
          animation-delay: 1.1s;
        }
        .flower__leafs--2 {
          animation-delay: 1.4s;
        }
        .flower__leafs--3 {
          animation-delay: 1.7s;
        }
        .flower__leafs--4 {
          animation-delay: 2.0s;
        }
        .flower__leafs--5 {
          animation-delay: 2.0s;
        }
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
          box-shadow: inset 0 0 1vmin rgba(255, 255, 255, 0.7), 
                      0 0 3vmin rgba(255, 215, 0, 0.4);
          z-index: 2;
        }
        .flower__leaf--1 {
          transform: translate(-50%, -10%) rotate(-45deg);
        }
        .flower__leaf--2 {
          transform: translate(-50%, -10%) rotate(-15deg);
        }
        .flower__leaf--3 {
          transform: translate(-50%, -10%) rotate(15deg);
        }
        .flower__leaf--4 {
          transform: translate(-50%, -10%) rotate(45deg);
        }
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
            ),
            radial-gradient(circle at center, #8b4513, #654321);
        }
        .flower__line {
          height: 55vmin;
          width: 2vmin;
          background-image: linear-gradient(
              to left,
              rgb(0, 0, 0, 0.3),
              transparent,
              rgba(255, 255, 255, 0.2)
            ),
            linear-gradient(to top, transparent 10%, #2d5016, #4a7c23, #6b8e23);
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
        .flower__line__leaf--1 {
          transform: rotate(70deg) rotateY(30deg);
        }
        .flower__line__leaf--2 {
          top: 45%;
          transform: rotate(70deg) rotateY(30deg);
        }
        .flower__line__leaf--3,
        .flower__line__leaf--4{
          border-top-right-radius: 0;
          border-bottom-left-radius: 0;
          border-top-left-radius: var(--h);
          border-bottom-right-radius: var(--h);
          left: -460%;
          top: 12%;
          transform: rotate(-70deg) rotateY(30deg);
        }
        .flower__line__leaf--4 {
          top: 40%;
        }
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
        .flower__light:nth-child(odd) {
          background-color: #654321;
        }
        .flower__light--1 { left: -2vmin; animation-delay: 1s; }
        .flower__light--2 { left: 3vmin; animation-delay: 0.5s; }
        .flower__light--3 { left: -6vmin; animation-delay: 0.3s; }
        .flower__light--4 { left: 6vmin; animation-delay: 0.9s; }
        .flower__light--5 { left: -1vmin; animation-delay: 1.5s; }
        .flower__light--6 { left: -4vmin; animation-delay: 3s; }
        .flower__light--7 { left: 3vmin; animation-delay: 2s; }
        .flower__light--8 { left: -6vmin; animation-delay: 3.5s; }
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
        .flower__grass--1 {
          animation: moving-grass 2s linear infinite;
        }
        .flower__grass--2 {
          left: 2vmin;
          bottom: 10vmin;
          transform: scale(0.5) rotate(75deg) rotateX(10deg) rotateY(-200deg);
          opacity: 0.8;
          z-index: 0;
          animation: moving-grass--2 1.5s linear infinite;
        }
        .flower__grass--3 {
          left: -25vmin;
          bottom: 8vmin;
          transform: scale(0.7) rotate(-30deg) rotateY(45deg);
          opacity: 0.9;
          z-index: 15;
          animation: moving-grass--3 2.2s linear infinite;
        }
        .flower__grass--4 {
          left: -35vmin;
          bottom: 15vmin;
          transform: scale(0.4) rotate(60deg) rotateX(15deg) rotateY(-180deg);
          opacity: 0.7;
          z-index: 5;
          animation: moving-grass--4 1.8s linear infinite;
        }
        .flower__grass--5 {
          left: -18vmin;
          bottom: 6vmin;
          transform: scale(0.6) rotate(-60deg) rotateY(60deg);
          opacity: 0.85;
          z-index: 12;
          animation: moving-grass--5 2.5s linear infinite;
        }
        .flower__grass--6 {
          left: 25vmin;
          bottom: 9vmin;
          transform: scale(0.65) rotate(35deg) rotateY(-45deg);
          opacity: 0.9;
          z-index: 15;
          animation: moving-grass--6 2.3s linear infinite;
        }
        .flower__grass--7 {
          left: 35vmin;
          bottom: 14vmin;
          transform: scale(0.45) rotate(-70deg) rotateX(20deg) rotateY(170deg);
          opacity: 0.75;
          z-index: 8;
          animation: moving-grass--7 1.9s linear infinite;
        }
        .flower__grass--8 {
          left: 18vmin;
          bottom: 5vmin;
          transform: scale(0.55) rotate(50deg) rotateY(-70deg);
          opacity: 0.8;
          z-index: 10;
          animation: moving-grass--8 2.1s linear infinite;
        }
        .flower__grass--9 {
          left: -45vmin;
          bottom: 20vmin;
          transform: scale(0.3) rotate(20deg) rotateY(90deg);
          opacity: 0.6;
          z-index: 2;
          animation: moving-grass--9 1.6s linear infinite;
        }
        .flower__grass--10 {
          left: 42vmin;
          bottom: 18vmin;
          transform: scale(0.35) rotate(-45deg) rotateY(-120deg);
          opacity: 0.65;
          z-index: 3;
          animation: moving-grass--10 2.0s linear infinite;
        }
        .flower__grass--top {
          width: 7vmin;
          height: 10vmin;
          border-top-right-radius: 100%;
          border-right: var(--line-w) solid var(--c);
          transform-origin: bottom center;
          transform: rotate(-2deg);
        }
        .flower__grass--bottom {
          margin-top: -2px;
          width: var(--line-w);
          height: 25vmin;
          background-image: linear-gradient(to top, transparent, var(--c));
        }
        .flower__grass__leaf {
          --size: 10vmin;
          position: absolute;
          width: calc(var(--size) * 2.1);
          height: var(--size);
          border-top-left-radius: var(--size);
          border-top-right-radius: var(--size);
          background-image: linear-gradient(
            to top,
            transparent,
            transparent 30%,
            var(--c)
          );
          z-index: 100;
        }
        .flower__grass__leaf--1 {
          top: -6%;
          left: 30%;
          --size: 6vmin;
          transform: rotate(-20deg);
          animation: growing-grass-ans--1 var(--speed-leaf) 2.6s backwards;
        }
        .flower__grass__leaf--2 {
          top: -5%;
          left: -110%;
          --size: 6vmin;
          transform: rotate(10deg);
          animation: growing-grass-ans--2 var(--speed-leaf) 2.4s linear backwards;
        }
        .flower__grass__leaf--3 {
          top: 5%;
          left: 60%;
          --size: 8vmin;
          transform: rotate(-18deg) rotateX(-20deg);
          animation: growing-grass-ans--3 var(--speed-leaf) 2.2s linear backwards;
        }
        .flower__grass__leaf--4 {
          top: 6%;
          left: -135%;
          --size: 8vmin;
          transform: rotate(2deg);
          animation: growing-grass-ans--4 var(--speed-leaf) 2s linear backwards;
        }
        .flower__grass__leaf--5 {
          top: 20%;
          left: 60%;
          --size: 10vmin;
          transform: rotate(-24deg) rotateX(-20deg);
          animation: growing-grass-ans--5 var(--speed-leaf) 1.8s linear backwards;
        }
        .flower__grass__leaf--6 {
          top: 22%;
          left: -180%;
          --size: 10vmin;
          transform: rotate(10deg);
          animation: growing-grass-ans--6 var(--speed-leaf) 1.6s linear backwards;
        }
        .flower__grass__leaf--7 {
          top: 39%;
          left: 70%;
          --size: 10vmin;
          transform: rotate(-10deg);
          animation: growing-grass-ans--7 var(--speed-leaf) 1.4s linear backwards;
        }
        .flower__grass__leaf--8 {
          top: 40%;
          left: -215%;
          --size: 11vmin;
          transform: rotate(10deg);
          animation: growing-grass-ans--8 var(--speed-leaf) 1.2s linear backwards;
        }
        .flower__grass__overlay {
          position: absolute;
          top: -10%;
          right: 0%;
          width: 100%;
          height: 100%;
          background-color: rgba(0, 0, 0, 0.6);
          filter: blur(1.5vmin);
          z-index: 100;
        }
        /* === RESTO DEL CÓDIGO ORIGINAL SIN TOCAR === */
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
        /* === KEYFRAMES NUEVOS === */
        @keyframes growing-grass-ans {
          0% {
            transform: scale(0);
          }
        }
        @keyframes growing-grass-ans--1 {
          0% {
            transform-origin: bottom left;
            transform: rotate(-20deg) scale(0);
          }
        }
        @keyframes growing-grass-ans--2 {
          0% {
            transform-origin: bottom right;
            transform: rotate(10deg) scale(0);
          }
        }
        @keyframes growing-grass-ans--3 {
          0% {
            transform-origin: bottom left;
            transform: rotate(-18deg) rotateX(-20deg) scale(0);
          }
        }
        @keyframes growing-grass-ans--4 {
          0% {
            transform-origin: bottom right;
            transform: rotate(2deg) scale(0);
          }
        }
        @keyframes growing-grass-ans--5 {
          0% {
            transform-origin: bottom left;
            transform: rotate(-24deg) rotateX(-20deg) scale(0);
          }
        }
        @keyframes growing-grass-ans--6 {
          0% {
            transform-origin: bottom right;
            transform: rotate(10deg) scale(0);
          }
        }
        @keyframes growing-grass-ans--7 {
          0% {
            transform-origin: bottom left;
            transform: rotate(-10deg) scale(0);
          }
        }
        @keyframes growing-grass-ans--8 {
          0% {
            transform-origin: bottom right;
            transform: rotate(10deg) scale(0);
          }
        }
        @keyframes sunflower-seeds {
          0% {
            opacity: 0;
            transform: translateY(0vmin) rotate(0deg);
          }
          20% {
            opacity: 1;
            transform: translateY(-3vmin) translateX(-1vmin) rotate(45deg);
          }
          40% {
            opacity: 1;
            transform: translateY(-8vmin) translateX(1vmin) rotate(90deg);
          }
          60% {
            transform: translateY(-12vmin) translateX(-1vmin) rotate(135deg);
          }
          80% {
            transform: translateY(-16vmin) translateX(2vmin) rotate(180deg);
            opacity: 0.5;
          }
          100% {
            transform: translateY(-25vmin) rotate(225deg);
            opacity: 0;
          }
        }
        @keyframes moving-flower-1 {
          0%, 100% { transform: rotate(2deg); }
          50% { transform: rotate(-2deg); }
        }
        @keyframes moving-flower-2 {
          0%, 100% { transform: rotate(18deg); }
          50% { transform: rotate(14deg); }
        }
        @keyframes moving-flower-3 {
          0%, 100% { transform: rotate(-18deg); }
          50% { transform: rotate(-20deg) rotateY(-10deg); }
        }
        @keyframes moving-flower-4 {
          0%, 100% { transform: rotate(9deg); }
          50% { transform: rotate(12deg) rotateY(9deg); }
        }
        @keyframes moving-flower-5 {
          0%, 100% { transform: rotate(-5deg); }
          50% { transform: rotate(-11deg) rotateY(5deg); }
        }
        @keyframes blooming-leaf-right {
          0% {
            transform-origin: left;
            transform: rotate(70deg) rotateY(30deg) scale(0);
          }
        }
        @keyframes blooming-leaf-left {
          0% {
            transform-origin: right;
            transform: rotate(-70deg) rotateY(30deg) scale(0);
          }
        }
        @keyframes grow-flower-tree {
          0% {
            height: 0;
            border-radius: 1vmin;
          }
        }
        @keyframes blooming-flower {
          0% {
            transform: scale(0);
          }
        }
        @keyframes moving-grass {
          0%, 100% { transform: rotate(-48deg) rotateY(40deg); }
          50% { transform: rotate(-50deg) rotateY(40deg); }
        }
        @keyframes moving-grass--2 {
          0%, 100% { transform: scale(0.5) rotate(75deg) rotateX(10deg) rotateY(-200deg); }
          50% { transform: scale(0.5) rotate(79deg) rotateX(10deg) rotateY(-200deg); }
        }
        @keyframes moving-grass--3 {
          0%, 100% { transform: scale(0.7) rotate(-30deg) rotateY(45deg); }
          50% { transform: scale(0.7) rotate(-33deg) rotateY(50deg); }
        }
        @keyframes moving-grass--4 {
          0%, 100% { transform: scale(0.4) rotate(60deg) rotateX(15deg) rotateY(-180deg); }
          50% { transform: scale(0.4) rotate(63deg) rotateX(18deg) rotateY(-175deg); }
        }
        @keyframes moving-grass--5 {
          0%, 100% { transform: scale(0.6) rotate(-60deg) rotateY(60deg); }
          50% { transform: scale(0.6) rotate(-57deg) rotateY(65deg); }
        }
        @keyframes moving-grass--6 {
          0%, 100% { transform: scale(0.65) rotate(35deg) rotateY(-45deg); }
          50% { transform: scale(0.65) rotate(38deg) rotateY(-40deg); }
        }
        @keyframes moving-grass--7 {
          0%, 100% { transform: scale(0.45) rotate(-70deg) rotateX(20deg) rotateY(170deg); }
          50% { transform: scale(0.45) rotate(-67deg) rotateX(23deg) rotateY(175deg); }
        }
        @keyframes moving-grass--8 {
          0%, 100% { transform: scale(0.55) rotate(50deg) rotateY(-70deg); }
          50% { transform: scale(0.55) rotate(53deg) rotateY(-65deg); }
        }
        @keyframes moving-grass--9 {
          0%, 100% { transform: scale(0.3) rotate(20deg) rotateY(90deg); }
          50% { transform: scale(0.3) rotate(23deg) rotateY(95deg); }
        }
        @keyframes moving-grass--10 {
          0%, 100% { transform: scale(0.35) rotate(-45deg) rotateY(-120deg); }
          50% { transform: scale(0.35) rotate(-42deg) rotateY(-115deg); }
        }

        /* === NUEVO: BOTÓN DE VER FOTOS (AJUSTADO MÁS ARRIBA) === */
        .photos-btn {
            position: fixed;
            top: 58%; /* Ajustado más arriba, justo debajo de la carta */
            left: 50%;
            transform: translateX(-50%);
            z-index: 1001;
            padding: 16px 36px;
            background: linear-gradient(135deg, #ffd700, #ff8c00);
            color: #333;
            font-family: 'Dancing Script', cursive;
            font-size: 2.4vmin;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 0 25px rgba(255, 215, 0, 0.7), 0 0 50px rgba(255, 215, 0, 0.3);
            transition: all 0.3s ease;
            outline: none;
            letter-spacing: 1.5px;
        }
        .photos-btn:hover {
            transform: translateX(-50%) scale(1.08);
            box-shadow: 0 0 30px rgba(255, 215, 0, 0.9), 0 0 60px rgba(255, 215, 0, 0.5);
            background: linear-gradient(135deg, #ffed4e, #ffa500);
        }
        .photos-btn:active {
            transform: translateX(-50%) scale(0.98);
        }

        /* === NUEVO: GALERÍA MODAL (LAYOUT 2x2) === */
        .gallery-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.95);
            z-index: 9999;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            padding: 20px;
            backdrop-filter: blur(5px);
        }
        .gallery-modal.active {
            display: flex;
        }
        .gallery-header {
            position: absolute;
            top: 20px;
            width: 100%;
            text-align: center;
            color: #ffd700;
            font-family: 'Dancing Script', cursive;
            font-size: 4vmin; /* ¡Más grande como pediste! */
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.9);
            z-index: 10;
            letter-spacing: 2px;
        }
        .close-gallery {
            position: absolute;
            top: 20px;
            right: 30px;
            font-size: 4vmin;
            color: #ffd700;
            cursor: pointer;
            z-index: 10;
            background: none;
            border: none;
            padding: 5px;
        }
        .close-gallery:hover {
            color: #ffed4e;
            transform: scale(1.1);
        }
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr); /* 2 columnas */
            grid-template-rows: repeat(2, 1fr); /* 2 filas */
            gap: 25px;
            max-width: 1200px;
            width: 90%;
            height: 70vh;
            margin-top: 100px;
            padding: 20px;
        }
        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 20px;
            box-shadow: 0 0 20px rgba(255, 215, 0, 0.4);
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.2, 0.8, 0.8, 0.2);
            height: 100%;
        }
        .gallery-item:hover {
            transform: translateY(-15px) scale(1.03);
            box-shadow: 0 0 30px rgba(255, 215, 0, 0.7);
        }
        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s ease;
        }
        .gallery-item:hover img {
            transform: scale(1.15);
        }
        .gallery-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to top, rgba(0,0,0,0.6), transparent);
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        .gallery-item:hover::before {
            opacity: 1;
        }

        /* === NUEVO: IMAGEN EN ZOOM MODAL === */
        .zoom-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.95);
            z-index: 10000;
            justify-content: center;
            align-items: center;
            backdrop-filter: blur(5px);
        }
        .zoom-modal.active {
            display: flex;
        }
        .zoom-content {
            max-width: 90%;
            max-height: 90%;
            animation: zoomIn 0.5s ease;
        }
        .zoom-content img {
            max-width: 100%;
            max-height: 90vh;
            border-radius: 16px;
            box-shadow: 0 0 40px rgba(255, 215, 0, 0.9);
            border: 4px solid #ffd700;
        }
        .close-zoom {
            position: absolute;
            top: 30px;
            right: 40px;
            font-size: 5vmin;
            color: #ffd700;
            cursor: pointer;
            z-index: 10;
            background: none;
            border: none;
        }
        .close-zoom:hover {
            color: #ffed4e;
            transform: rotate(90deg);
            transition: all 0.3s ease;
        }
        @keyframes zoomIn {
            from { transform: scale(0.8); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        /* === NUEVO: BOTÓN DE CONTROL DE MÚSICA === */
        .music-control {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: rgba(255, 215, 0, 0.9);
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 2000;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.7);
            transition: all 0.3s ease;
            font-size: 28px;
            color: #333;
        }
        .music-control:hover {
            transform: scale(1.1);
            box-shadow: 0 0 25px rgba(255, 215, 0, 0.9);
        }
        .music-control.playing {
            animation: pulse 1.5s infinite;
        }
        @keyframes pulse {
            0% { box-shadow: 0 0 15px rgba(255, 215, 0, 0.7); }
            50% { box-shadow: 0 0 25px rgba(255, 215, 0, 0.9), 0 0 40px rgba(255, 215, 0, 0.6); }
            100% { box-shadow: 0 0 15px rgba(255, 215, 0, 0.7); }
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
    <!-- === NUEVO: BOTÓN DE VER FOTOS (AJUSTADO MÁS ARRIBA) === -->
    <button class="photos-btn" id="photosBtn">Ver Fotos 📸</button>
    <!-- === MENÚ DE 3 RAYAS === -->
    <div class="menu-btn" id="menuBtn">
        <span></span>
        <span></span>
        <span></span>
    </div>
    <div class="menu-panel" id="menuPanel">
        <h3>Información</h3>
        <p>Esta sorpresa a sido Desarrollado|Por| BerMatMods</p>
        <p>Diseño experiencias únicas con amor y código 💻✨</p>
        <a href="https://wa.me/51930569195" target="_blank">💬 Escríbeme en WhatsApp</a>
        <p>Para:Mi Reina Hermosa Briyidt</p>
        <p>Créditos: By AnthZz Berrocal BerMatMods © 2025</p>
    </div>
    <!-- === FLORES NUEVAS (REEMPLAZADAS - CONTENEDOR VACÍO) === -->
    <div class="flowers">
        <!-- Serán inyectadas por JS -->
    </div>
    <!-- === CRÉDITOS === -->
    <div class="credits">By AnthZz Berrocal BerMatMods</div>

    <!-- === NUEVO: GALERÍA MODAL === -->
    <div class="gallery-modal" id="galleryModal">
        <div class="gallery-header">Nuestros Momentos Preciosos 🌻</div>
        <button class="close-gallery" id="closeGallery">✕</button>
        <div class="gallery-grid" id="galleryGrid">
            <!-- Las imágenes se inyectarán aquí por JS -->
        </div>
    </div>

    <!-- === NUEVO: ZOOM MODAL === -->
    <div class="zoom-modal" id="zoomModal">
        <button class="close-zoom" id="closeZoom">✕</button>
        <div class="zoom-content">
            <img id="zoomImage" src="" alt="Imagen en zoom">
        </div>
    </div>

    <!-- === NUEVO: BOTÓN DE CONTROL DE MÚSICA === -->
    <button class="music-control" id="musicControl">🎵</button>

    <!-- === NUEVO: AUDIO === -->
    <audio id="backgroundMusic" src="https://dl.dropboxusercontent.com/scl/fi/xac2mz0t4homhkvkr1d5w/FLORES-AMARILLAS.mp3?rlkey=uush4yu80dlaz54tbfilgdnb5&st=d0wjojvs" preload="auto"></audio>

    <script>
        // Variables globales para música
        let musicPlayed = false;
        let isPlaying = false;
        const backgroundMusic = document.getElementById('backgroundMusic');
        const musicControl = document.getElementById('musicControl');

        // Función para reproducir música
        function playMusic() {
            backgroundMusic.play().then(() => {
                isPlaying = true;
                musicControl.textContent = '🔇';
                musicControl.classList.add('playing');
            }).catch(e => {
                console.log("Reproducción automática bloqueada. El usuario debe interactuar primero.");
            });
        }

        // Función para pausar música
        function pauseMusic() {
            backgroundMusic.pause();
            isPlaying = false;
            musicControl.textContent = '🎵';
            musicControl.classList.remove('playing');
        }

        // Alternar música al hacer clic en el botón
        musicControl.addEventListener('click', () => {
            if (isPlaying) {
                pauseMusic();
            } else {
                playMusic();
            }
        });

        // Reproducir música al interactuar por primera vez
        function playMusicOnce() {
            if (!musicPlayed) {
                playMusic();
                musicPlayed = true;
            }
        }

        // Detectar interacción del usuario (clic o toque)
        document.addEventListener('click', playMusicOnce);
        document.addEventListener('touchstart', playMusicOnce);

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
                "eres el amor de mi vida, 🌍💫",
                "Porque tú eres mi luz, mi calor, mi todo 💛",
                "Y en cada pétalo, hay una palabra de amor para ti 💌",
                "Con todo mi corazón...<br>Te Amo muchísimo mi reina Briyidth💛"
                "Atte: 👽AnthZz Berrocal👽" 
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

            // === INYECCIÓN DE LAS FLORES NUEVAS ===
            document.querySelector('.flowers').innerHTML = `
            <div class="flower flower--1">
              <div class="flower__leafs flower__leafs--1">
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
          `;
        };

        // === NUEVO: GALERÍA DE FOTOS ===
        const photoUrls = [
            'https://i.postimg.cc/YC1PLchN/1742316301125-2.jpg',
            'https://i.postimg.cc/bJGWJZbr/PSX-20250530-060357.jpg',
            'https://i.postimg.cc/wjVSb8gq/Screenshot-20250427-213138.jpg',
            'https://i.postimg.cc/N0CZB6KZ/Screenshot-20250810-134752.jpg'
        ];

        const photosBtn = document.getElementById('photosBtn');
        const galleryModal = document.getElementById('galleryModal');
        const closeGallery = document.getElementById('closeGallery');
        const galleryGrid = document.getElementById('galleryGrid');
        const zoomModal = document.getElementById('zoomModal');
        const closeZoom = document.getElementById('closeZoom');
        const zoomImage = document.getElementById('zoomImage');

        // Inyectar imágenes en la galería (layout 2x2)
        function loadGallery() {
            galleryGrid.innerHTML = '';
            photoUrls.forEach(url => {
                const item = document.createElement('div');
                item.className = 'gallery-item';
                const img = document.createElement('img');
                img.src = url;
                img.alt = 'Foto de recuerdo';
                item.appendChild(img);
                galleryGrid.appendChild(item);

                // Evento para abrir el zoom
                item.addEventListener('click', () => {
                    zoomImage.src = url;
                    zoomModal.classList.add('active');
                    playMusicOnce(); // Asegurar que la música suene
                });
            });
        }

        // Abrir galería
        photosBtn.addEventListener('click', () => {
            galleryModal.classList.add('active');
            loadGallery();
            playMusicOnce();
        });

        // Cerrar galería
        closeGallery.addEventListener('click', () => {
            galleryModal.classList.remove('active');
        });

        // Cerrar zoom
        closeZoom.addEventListener('click', () => {
            zoomModal.classList.remove('active');
        });

        // Cerrar zoom al hacer clic fuera de la imagen
        zoomModal.addEventListener('click', (e) => {
            if (e.target === zoomModal) {
                zoomModal.classList.remove('active');
            }
        });

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
            playMusicOnce(); // Asegurar música al hacer clic
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
            playMusicOnce();
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
