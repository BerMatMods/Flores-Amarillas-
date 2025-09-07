<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Las Flores Amarillas</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@400;600&display=swap" rel="stylesheet">

  <style>
    /* ===== RESET ===== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #fffaf6;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      overflow: hidden;
      font-family: 'Poppins', sans-serif;
      color: #444;
      position: relative;
    }

    /* ===== FONDO SUAVE DE ROSAS ===== */
    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: url('https://media2.giphy.com/media/v1.Y2lkPTZjMDliOTUyaXVrY3Z1aWtsczlldWhkaG4xZWw3N2pmanhheDR4dmQ5YWU1MG5peiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/BKqOqscntEIrm/giphy.gif') center center no-repeat;
      background-size: cover;
      opacity: 0.1;
      z-index: -2;
    }

    /* ===== PANTALLA DE CARGA ===== */
    #loading-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #fff9e6, #ffefc9);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      transition: opacity 1s ease-out;
    }

    .loading-title {
      font-family: 'Dancing Script', cursive;
      font-size: 3.5rem;
      color: #e69500;
      margin-bottom: 20px;
      text-shadow: 0 0 15px rgba(255, 204, 0, 0.6);
      text-align: center;
    }

    .progress-bar {
      width: 85%;
      max-width: 350px;
      height: 10px;
      background: #ffe5b8;
      border-radius: 5px;
      overflow: hidden;
      margin: 20px 0;
      box-shadow: inset 0 2px 6px rgba(0,0,0,0.1);
    }

    .progress {
      width: 0%;
      height: 100%;
      background: linear-gradient(90deg, #ffcc00, #ff9900, #ffcc00);
      border-radius: 5px;
      transition: width 0.3s ease;
    }

    .percentage {
      font-size: 1.3rem;
      color: #e69500;
      font-weight: 600;
      margin-bottom: 10px;
    }

    /* ===== DECORACIONES EN CARGA ===== */
    .loading-sunflower {
      position: absolute;
      font-size: 2.8rem;
      opacity: 0;
      pointer-events: none;
      z-index: 999;
      animation: floatUp 6s ease-in infinite;
    }
    @keyframes floatUp {
      0% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
      10% { opacity: 1; }
      90% { opacity: 1; }
      100% { transform: translateY(-20vh) rotate(360deg); opacity: 0; }
    }

    .yellow-heart {
      position: absolute;
      font-size: 2.2rem;
      color: #ffcc00;
      text-shadow: 0 0 8px rgba(255, 204, 0, 0.7);
      opacity: 0.9;
      pointer-events: none;
      z-index: 998;
      animation: rain linear infinite;
    }
    @keyframes rain {
      0% { transform: translateY(-10vh) rotate(0deg); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
    }

    .star {
      position: absolute;
      font-size: 1.8rem;
      color: #fffacd;
      text-shadow: 0 0 10px #fffacd;
      opacity: 0.8;
      pointer-events: none;
      z-index: 997;
      animation: sparkle 4s ease-in-out infinite;
    }
    @keyframes sparkle {
      0%, 100% { transform: translateY(100vh) scale(0.5); opacity: 0; }
      10% { opacity: 1; }
      50% { transform: translateY(50vh) scale(1.2); }
      90% { opacity: 1; }
      100% { transform: translateY(-20vh); opacity: 0; }
    }

    .petal {
      position: absolute;
      font-size: 2rem;
      color: #ffcc00;
      opacity: 0.7;
      pointer-events: none;
      z-index: 996;
      animation: swirl 7s linear infinite;
    }
    @keyframes swirl {
      0% { transform: translateY(100vh) rotate(0deg) scale(0); }
      20% { opacity: 1; transform: translateY(80vh) rotate(90deg) scale(1); }
      80% { opacity: 1; transform: translateY(20vh) rotate(270deg) scale(1); }
      100% { transform: translateY(0vh) rotate(360deg) scale(0); opacity: 0; }
    }

    /* Información en carga */
    .loading-footer {
      margin-top: 30px;
      text-align: center;
      font-family: 'Poppins', sans-serif;
      font-size: 1.1rem;
      color: #d48a00;
    }

    .whatsapp-link {
      color: #e69500;
      text-decoration: none;
      font-weight: 600;
      border-bottom: 2px solid #ffcc00;
      padding: 2px 4px;
      transition: all 0.3s ease;
    }
    .whatsapp-link:hover {
      background: #ffcc00;
      color: #fff;
      border-radius: 4px;
    }

    /* ===== CONTENIDO PRINCIPAL ===== */
    #main-content {
      display: none;
      opacity: 0;
      transition: opacity 1.2s ease;
      width: 100%;
      text-align: center;
      z-index: 10;
      padding: 20px;
    }

    /* ===== TÍTULO DE LAS FLORES AMARILLAS ===== */
    .title {
      font-family: 'Dancing Script', cursive;
      font-size: 5vmin;
      color: #ff8c00;
      margin-bottom: 30px;
      text-shadow: 0 0 10px rgba(255, 200, 0, 0.4);
    }

    /* ===== TARJETA DE CARTA - MÁS PEQUEÑA ===== */
    .card {
      background: rgba(255, 250, 250, 0.95);
      backdrop-filter: blur(10px);
      border: 2px solid #ffb6c1;
      box-shadow: 
        0 0 15px rgba(255, 182, 193, 0.6),
        0 0 30px rgba(255, 182, 193, 0.4);
      border-radius: 20px;
      padding: 20px;
      margin: 0 auto 60px;
      max-width: 400px; /* Ancho reducido */
      text-align: center;
      animation: pulse 2s infinite alternate;
    }

    @keyframes pulse {
      0% { box-shadow: 0 0 15px rgba(255, 182, 193, 0.6); }
      100% { box-shadow: 0 0 25px rgba(255, 182, 193, 0.8); }
    }

    .card h2 {
      font-family: 'Dancing Script', cursive;
      font-size: 3.2vmin;
      color: #d66a8f;
      margin-bottom: 15px;
      text-shadow: 0 0 5px rgba(255, 182, 193, 0.4);
    }

    .card p {
      font-size: 1.7vmin;
      line-height: 1.7;
      color: #555;
    }

    .emoji {
      font-size: 1.8vmin;
      margin: 0 4px;
    }

    /* ===== FLOR SIN RECUADRO ===== */
    .flower-bottom-container {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: flex-end;
      margin-top: 40px;
      margin-bottom: 30px;
    }

    .sunflower {
      position: relative;
      width: 120px;
      height: 200px;
      transform: scale(0.8);
      transform-origin: bottom center;
    }

    .flower_wrapper {
      position: absolute;
      left: 50%;
      bottom: 0;
      transform: translateX(-50%);
      animation: moving-flower-1 4s linear infinite;
    }

    .flower_stem {
      width: 2vmin;
      height: 65vmin;
      background-image: linear-gradient(to left top, #82ff86 20%, #144425, #104e1c);
      border-radius: 4vmin;
      margin-left: calc(50% - 1vmin);
    }

    .flower_center {
      position: absolute;
      top: 0vmin;
      left: 50%;
      z-index: 5;
      transform: translateX(-50%) rotate(-10deg);
      width: 20vmin;
      height: 20vmin;
      border-radius: 50%;
      background: radial-gradient(circle, #000, #ff5e00);
      animation: open-flower-middle 2s 0.4s backwards;
    }

    .flower_petal {
      position: absolute;
      left: 50%;
      z-index: 3;
      bottom: 55vmin;
      transform: translateX(-50%);
      width: 7vmin;
      height: 20vmin;
      background: radial-gradient(circle, #ff5e00, #ffbb00);
      clip-path: ellipse(50% 50% at 50% 50%);
      transform-origin: center bottom;
      animation: open-flower 2s 1s backwards;
    }

    .flower_petal-1 { border-radius: 50% 50% 50% / 80% 80% 20% 20%; }
    .flower_petal-2 { transform: translateX(-50%) rotate(-30deg); }
    .flower_petal-3 { transform: translateX(-50%) rotate(-60deg); }
    .flower_petal-4 { transform: translateX(-50%) rotate(-90deg); }
    .flower_petal-5 { transform: translateX(-50%) rotate(-120deg); }
    .flower_petal-6 { transform: translateX(-50%) rotate(-150deg); }
    .flower_petal-7 { transform: translateX(-50%) rotate(30deg); }
    .flower_petal-8 { transform: translateX(-50%) rotate(60deg); }
    .flower_petal-9 { transform: translateX(-50%) rotate(90deg); }
    .flower_petal-10 { transform: translateX(-50%) rotate(120deg); }
    .flower_petal-11 { transform: translateX(-50%) rotate(150deg); }
    .flower_petal-12 { transform: translateX(-50%) rotate(180deg); }

    .flower_leaf {
      position: absolute;
      width: 7vmin;
      height: 17vmin;
      background: radial-gradient(circle, #82ff86, #104e1c);
      border-radius: 10vmin 2vmin 10vmin 2vmin;
      transform-origin: center bottom;
    }

    .flower_leaf-1 { left: 60%; bottom: 18vmin; transform: translateX(-45%) rotate(80deg); }
    .flower_leaf-2 { left: 40%; bottom: 23vmin; transform: translateX(-55%) rotate(-80deg); }

    .flower_light {
      position: absolute;
      bottom: 70vmin;
      width: 1vmin;
      height: 1vmin;
      background-color: #fff800;
      border-radius: 50%;
      filter: blur(0.2vmin);
      animation: light-ans 4s linear infinite backwards;
    }

    .flower_light-1 { left: -2vmin; animation-delay: 1s; }
    .flower_light-2 { left: 3vmin; animation-delay: 0.5s; }
    .flower_light-3 { left: -6vmin; animation-delay: 0.3s; }
    .flower_light-4 { left: 6vmin; animation-delay: 0.9s; }
    .flower_light-5 { left: -1vmin; animation-delay: 1.5s; }
    .flower_light-6 { left: -4vmin; animation-delay: 3s; }
    .flower_light-7 { left: 3vmin; animation-delay: 2s; }
    .flower_light-8 { left: -6vmin; animation-delay: 3.5s; }

    /* ===== ANIMACIONES ===== */
    @keyframes moving-flower-1 {
      0%, 100% { transform: translateY(0) rotate(0deg); }
      50% { transform: translateY(-3vmin) rotate(1.5deg); }
    }

    @keyframes open-flower {
      0% { transform: translateX(-50%) rotate(0); opacity: 0; }
      100% { transform: translateX(-50%) rotate(0); opacity: 1; }
    }

    @keyframes open-flower-middle {
      0% { opacity: 0; transform: translateX(-50%) scale(0) rotate(-10deg); }
      100% { opacity: 1; transform: translateX(-50%) scale(1) rotate(-10deg); }
    }

    @keyframes light-ans {
      0% { opacity: 0; transform: translateY(0vmin); }
      25% { opacity: 1; transform: translateY(-5vmin) translateX(-2vmin); }
      50% { opacity: 1; transform: translateY(-15vmin) translateX(2vmin); filter: blur(0.2vmin); }
      75% { transform: translateY(-20vmin) translateX(-2vmin); filter: blur(0.2vmin); }
      100% { transform: translateY(-30vmin); opacity: 0; filter: blur(1vmin); }
    }

    /* ===== FIRMA FINAL ===== */
    .credits {
      margin-top: 30px;
      font-family: 'Dancing Script', cursive;
      font-size: 2.6vmin;
      color: #d48a00;
      text-shadow: 0 0 5px rgba(255, 140, 0, 0.3);
    }
  </style>
</head>
<body>

  <!-- ===== PANTALLA DE CARGA ===== -->
  <div id="loading-screen">
    <h2 class="loading-title">🌷 Cargando tu sorpresa especial... 💖</h2>
    <div class="progress-bar">
      <div class="progress" id="progress"></div>
    </div>
    <p class="percentage" id="percentage">0%</p>

    <script>
      function createSunflower() { const el = document.createElement('div'); el.className = 'loading-sunflower'; el.innerText = '🌻'; el.style.left = Math.random() * 100 + 'vw'; document.body.appendChild(el); setTimeout(() => el.remove(), 6000); }
      function createHeart() { const el = document.createElement('div'); el.className = 'yellow-heart'; el.innerText = ['💛', '💖', '💗', '✨', '🔶'][Math.floor(Math.random() * 5)]; el.style.left = Math.random() * 100 + 'vw'; el.style.animationDuration = (Math.random() * 5 + 4) + 's'; document.body.appendChild(el); setTimeout(() => el.remove(), 8000); }
      function createStar() { const el = document.createElement('div'); el.className = 'star'; el.innerText = '⭐'; el.style.left = Math.random() * 100 + 'vw'; el.style.animationDuration = (Math.random() * 4 + 3) + 's'; document.body.appendChild(el); setTimeout(() => el.remove(), 6000); }
      function createPetal() { const el = document.createElement('div'); el.className = 'petal'; el.innerText = '🌼'; el.style.left = Math.random() * 100 + 'vw'; el.style.animationDuration = (Math.random() * 6 + 5) + 's'; document.body.appendChild(el); setTimeout(() => el.remove(), 7000); }

      setInterval(createSunflower, 800);
      setInterval(createHeart, 600);
      setInterval(createStar, 1000);
      setInterval(createPetal, 1200);
    </script>

    <!-- WhatsApp en carga -->
    <div class="loading-footer">
      <p>By <strong>AnthZz Berrocal BerMatMods</strong></p>
      <p>
        ¿Quieres uno personalizado? 
        <a href="https://wa.me/51930569195?text=Hola%20AnthZz,%20quisiera%20una%20sorpresa%20como%20esta%20para%20alguien%20especial%20💛" 
           class="whatsapp-link" target="_blank">
           Escríbeme al WhatsApp
        </a>
      </p>
    </div>
  </div>

  <!-- ===== CONTENIDO PRINCIPAL ===== -->
  <div id="main-content">

    <!-- Título principal -->
    <h1 class="title">Las Flores Amarillas</h1>

    <!-- Tarjeta pequeña -->
    <div class="card">
      <h2>Para La Mujer Más Hermosa del Mundo</h2>
      <p>
        🌼 En este día especial, quiero que sepas que eres como una flor amarilla: 
        brillante, hermosa y llena de vida. 💛<br><br>
        Tu sonrisa ilumina mis días, tu amor llena mi alma, 
        y cada momento contigo es un regalo. 🌻<br><br>
        <span class="emoji">💌</span> Hoy y siempre, mi corazón es solo tuyo. <span class="emoji">💌</span>
      </p>
    </div>

    <!-- Flor sin marco -->
    <div class="flower-bottom-container">
      <div class="sunflower">
        <div class="flower_wrapper">
          <div class="flower_stem"></div>
          <div class="flower_center"></div>
          <div class="flower_petal flower_petal-1"></div>
          <div class="flower_petal flower_petal-2"></div>
          <div class="flower_petal flower_petal-3"></div>
          <div class="flower_petal flower_petal-4"></div>
          <div class="flower_petal flower_petal-5"></div>
          <div class="flower_petal flower_petal-6"></div>
          <div class="flower_petal flower_petal-7"></div>
          <div class="flower_petal flower_petal-8"></div>
          <div class="flower_petal flower_petal-9"></div>
          <div class="flower_petal flower_petal-10"></div>
          <div class="flower_petal flower_petal-11"></div>
          <div class="flower_petal flower_petal-12"></div>
          <div class="flower_leaf flower_leaf-1"></div>
          <div class="flower_leaf flower_leaf-2"></div>
          <div class="flower_light flower_light-1"></div>
          <div class="flower_light flower_light-2"></div>
          <div class="flower_light flower_light-3"></div>
          <div class="flower_light flower_light-4"></div>
          <div class="flower_light flower_light-5"></div>
          <div class="flower_light flower_light-6"></div>
          <div class="flower_light flower_light-7"></div>
          <div class="flower_light flower_light-8"></div>
        </div>
      </div>
    </div>

    <!-- Firma final -->
    <div class="credits">
      By AnthZz Berrocal BerMatMods
    </div>

    <!-- Interacción con clic -->
    <script>
      function createSunflowerExplosion(x, y) {
        for (let i = 0; i < 15; i++) {
          const sunflower = document.createElement('div');
          sunflower.innerText = '🌻';
          sunflower.style.position = 'absolute';
          sunflower.style.fontSize = '2.5vmin';
          sunflower.style.pointerEvents = 'none';
          sunflower.style.zIndex = '100';
          sunflower.style.left = x + 'px';
          sunflower.style.top = y + 'px';
          sunflower.style.opacity = '1';

          const angle = Math.random() * 360;
          const distance = Math.random() * 120;
          const tx = Math.cos(angle) * distance;
          const ty = Math.sin(angle) * distance;

          document.body.appendChild(sunflower);

          setTimeout(() => {
            sunflower.style.transition = 'transform 1s ease-out, opacity 1s ease-out';
            sunflower.style.transform = `translate(${tx}px, ${ty}px) rotate(${Math.random() * 360}deg) scale(1.5)`;
            sunflower.style.opacity = '0';
          }, 10);

          setTimeout(() => sunflower.remove(), 1100);
        }
      }

      document.body.addEventListener('click', (e) => createSunflowerExplosion(e.clientX, e.clientY));
      document.body.addEventListener('touchstart', (e) => {
        for (let touch of e.touches) createSunflowerExplosion(touch.clientX, touch.clientY);
      });
    </script>

  </div>

  <!-- ===== CARGA ===== -->
  <script>
    const loadingScreen = document.getElementById('loading-screen');
    const progress = document.getElementById('progress');
    const percentage = document.getElementById('percentage');
    const mainContent = document.getElementById('main-content');

    let current = 0;
    const interval = setInterval(() => {
      current += 1;
      progress.style.width = current + '%';
      percentage.textContent = current + '%';

      if (current >= 100) {
        clearInterval(interval);
        loadingScreen.style.opacity = 0;
        setTimeout(() => {
          loadingScreen.style.display = 'none';
          mainContent.style.display = 'block';
          setTimeout(() => mainContent.style.opacity = 1, 50);
        }, 800);
      }
    }, 60);
  </script>

</body>
</html>
