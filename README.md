<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Escena Mágica</title>
  <style>
    :root {
      --color-bg-dark: #18132a;
      --color-sunflower: #ffe052;
      --color-heart: #e2425c;
      --color-sparkle: #fff9c1;
      --color-butterfly-wing1: #b2e2ff;
      --color-butterfly-wing2: #fee2b3;
    }

    body {
      margin: 0;
      background: linear-gradient(-45deg, #18132a, #2a0038, #5a2c2c);
      background-size: 400% 400%;
      animation: gradient-shift 15s ease infinite;
      overflow: hidden;
      height: 100vh;
      width: 100vw;
      font-family: 'Segoe UI', Arial, sans-serif;
    }

    .scene {
      position: relative;
      width: 100%;
      height: 100%;
    }

    .girasol-container {
      position: absolute;
      display: flex;
      flex-direction: column;
      align-items: center;
      bottom: 0;
      z-index: 5;
    }

    .petalo {
      position: absolute;
      width: 40%;
      height: 30%;
      background: radial-gradient(circle at center, #fffbe2 20%, var(--color-sunflower) 60%, #f5a623 100%);
      border-radius: 50% 70% 50% 70% / 60% 70% 60% 70%;
      box-shadow: 0 2px 14px var(--color-sunflower);
      opacity: 0.98;
      transform-origin: 50% 100%;
      transform: translateY(-50%) rotate(calc(var(--petal-rotation) * 1deg));
    }
    .petalo:nth-child(1)  { --petal-rotation: 0; }
    .petalo:nth-child(2)  { --petal-rotation: 30; }
    .petalo:nth-child(3)  { --petal-rotation: 60; }
    .petalo:nth-child(4)  { --petal-rotation: 90; }
    .petalo:nth-child(5)  { --petal-rotation: 120; }
    .petalo:nth-child(6)  { --petal-rotation: 150; }
    .petalo:nth-child(7)  { --petal-rotation: 180; }
    .petalo:nth-child(8)  { --petal-rotation: 210; }
    .petalo:nth-child(9)  { --petal-rotation: 240; }
    .petalo:nth-child(10) { --petal-rotation: 270; }
    .petalo:nth-child(11) { --petal-rotation: 300; }
    .petalo:nth-child(12) { --petal-rotation: 330; }

    .centro {
      position: absolute;
      width: 50%;
      height: 50%;
      background: radial-gradient(circle at 62% 42%, #7a4a12 68%, #e5b95b 95%);
      border-radius: 50%;
      z-index: 3;
      box-shadow: 0 0 16px var(--color-sunflower), 0 0 42px rgba(255, 224, 82, 0.2);
    }

    .tallo {
      width: 13%;
      min-height: 50px;
      background: linear-gradient(to bottom, #356b1c 60%, #7fc959 100%);
      border-radius: 7px 7px 40px 40px / 9px 9px 90px 90px;
      box-shadow: 0 8px 16px rgba(30, 50, 17, 0.533);
      flex-shrink: 0;
      margin-top: 15%;
    }

    @keyframes sway {
      0% { transform: rotate(0deg); }
      50% { transform: rotate(4deg); }
      100% { transform: rotate(0deg); }
    }
    .girasol-container.animate {
      animation: sway 10s infinite ease-in-out;
    }
    
    .girasol-1 { left: 10%; height: 260px; width: 180px; animation-delay: 0s; } .girasol-1 .tallo { height: 140px; }
    .girasol-2 { left: 25%; height: 220px; width: 120px; animation-delay: 1.5s; } .girasol-2 .tallo { height: 100px; }
    .girasol-3 { left: 45%; height: 190px; width: 90px; animation-delay: 3s; } .girasol-3 .tallo { height: 70px; }
    .girasol-4 { left: 68%; height: 240px; width: 140px; animation-delay: 2s; } .girasol-4 .tallo { height: 110px; }
    .girasol-5 { left: 80%; height: 205px; width: 105px; animation-delay: 4.5s; } .girasol-5 .tallo { height: 85px; }
    .girasol-6 { left: 55%; height: 250px; width: 170px; animation-delay: 1s; } .girasol-6 .tallo { height: 130px; }

    /* --- Corazones --- */
    .heart {
      position: absolute;
      width: 30px;
      height: 27px;
      z-index: 20;
      opacity: 0;
      pointer-events: none;
      filter: drop-shadow(0 0 6px rgba(255, 255, 255, 0.4));
      transform-origin: center bottom;
      animation: heart-float 6s infinite ease-out forwards;
    }
    .heart-shape {
      position: absolute;
      width: 100%;
      height: 100%;
      left: 0; top: 0;
      transform: rotate(-45deg);
      background: var(--color-heart);
      border-radius: 60% 60% 60% 60% / 60% 60% 60% 60%;
      box-shadow: 0 0 11px rgba(226, 66, 92, 0.6);
    }
    .heart-shape::before, .heart-shape::after {
      content: "";
      position: absolute;
      width: 50%;
      height: 80%;
      background: radial-gradient(circle at 60% 20%, #fff7, var(--color-heart) 90%);
      border-radius: 60% 60% 0 0;
      top: 0;
    }
    .heart-shape::before { left: 0; }
    .heart-shape::after { left: 50%; }

    @keyframes heart-float {
      0% { transform: translateY(0) scale(0.5); opacity: 0; }
      10% { opacity: 0.8; transform: translateY(-30px) scale(0.8); }
      80% { opacity: 0.6; transform: translateY(-200px) scale(1.1); }
      100% { transform: translateY(-300px) scale(1.2); opacity: 0; }
    }
    .heart-1 { left: 15%; bottom: 10%; animation-delay: 0s; }
    .heart-2 { left: 30%; bottom: 5%; animation-delay: 2s; }
    .heart-3 { left: 50%; bottom: 12%; animation-delay: 1.2s; }
    .heart-4 { left: 70%; bottom: 8%; animation-delay: 3s; }
    .heart-5 { left: 85%; bottom: 3%; animation-delay: 1.7s; }
    .heart-6 { left: 60%; bottom: 15%; animation-delay: 2.7s; }

    /* --- Brillitos --- */
    .sparkle {
      position: absolute;
      width: 7px; height: 7px;
      border-radius: 50%;
      background: var(--color-sparkle);
      box-shadow: 0 0 20px 6px rgba(255, 249, 193, 0.6), 0 0 6px var(--color-sunflower);
      opacity: 0.95;
      z-index: 12;
      animation: sparkle 2.6s infinite ease-in-out;
    }

    .girasol-container:hover .sparkle {
      animation: sparkle-glow 1s forwards;
    }
    @keyframes sparkle-glow {
      0% { transform: scale(1); opacity: 0.8; }
      50% { transform: scale(2.5); opacity: 0.2; }
      100% { transform: scale(0); opacity: 0; }
    }

    @keyframes sparkle {
      0%, 100% { transform: scale(1); opacity: 0.8;}
      40% { transform: scale(1.7); opacity: 1;}
      60% { transform: scale(0.7); opacity: 0.4;}
    }
    
    .sparkle-1 { top: 17%; left: 14%; animation-delay: 0.3s; }
    .sparkle-2 { top: 23%; left: 62%; animation-delay: 1s; }
    .sparkle-3 { top: 37%; left: 26%; animation-delay: 1.5s; }
    .sparkle-4 { top: 15%; left: 45%; animation-delay: 2.1s; }
    .sparkle-5 { top: 12%; left: 84%; animation-delay: 2.7s; }
    .sparkle-6 { top: 80%; left: 16%; animation-delay: 1.2s; }
    .sparkle-7 { top: 72%; left: 65%; animation-delay: 2.4s; }
    .sparkle-8 { top: 47%; left: 80%; animation-delay: 1.7s; }

    /* --- Mariposas --- */
    .butterfly {
      position: absolute;
      width: 34px; height: 28px;
      z-index: 35;
      pointer-events: none;
      animation: butterfly-fly 12s linear infinite;
      filter: drop-shadow(0 0 8px rgba(255, 255, 255, 0.2));
    }
    .wings::before, .wings::after {
      content: "";
      position: absolute;
      width: 17px; height: 24px;
      border-radius: 70% 90% 60% 70% / 90% 80% 60% 70%;
      top: 2px;
      transform: rotate(-13deg);
      box-shadow: 0 0 12px rgba(246, 214, 255, 0.6);
      opacity: 0.82;
    }
    .wings::before {
      background: linear-gradient(135deg, var(--color-butterfly-wing1) 60%, var(--color-butterfly-wing2) 100%);
      left: 0;
    }
    .wings::after {
      background: linear-gradient(135deg, var(--color-butterfly-wing2) 60%, var(--color-butterfly-wing1) 100%);
      left: 17px;
      transform: scaleX(-1) rotate(-13deg);
    }
    .body {
      position: absolute;
      left: 13px; top: 8px;
      width: 7px; height: 16px;
      background: #3a1831;
      border-radius: 60% 60% 50% 50% / 28% 28% 70% 70%;
      z-index: 2;
      box-shadow: 0 0 8px rgba(255, 255, 255, 0.47);
    }
    .antenna {
      position: absolute;
      width: 12px; height: 12px;
      border: 2px solid #e8cefd;
      border-bottom: none;
      border-radius: 60% 60% 0 0;
      top: -10px;
      z-index: 2;
    }
    .antenna.left { left: 7px; transform: rotate(-16deg); }
    .antenna.right { left: 17px; transform: scaleX(-1) rotate(-16deg); }

    @keyframes butterfly-fly {
      0%   { transform: translate(0, 0) rotate(0deg); }
      20%  { transform: translate(60px, -80px) rotate(15deg); }
      40%  { transform: translate(10px, -150px) rotate(-10deg); }
      60%  { transform: translate(-70px, -100px) rotate(-20deg); }
      80%  { transform: translate(-20px, -30px) rotate(5deg); }
      100% { transform: translate(0, 0) rotate(0deg); }
    }
    .butterfly-1 { left: 22%; top: 38%; animation-delay: 0s; }
    .butterfly-2 { left: 42%; top: 20%; animation-delay: 2.2s; }
    .butterfly-3 { left: 73%; top: 28%; animation-delay: 4.1s; }
    .butterfly-4 { left: 57%; top: 12%; animation-delay: 6s; }

    @keyframes gradient-shift {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
  </style>
</head>
<body>
  <div class="scene">
    <div class="girasol-container girasol-1 animate">
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="centro"></div>
      <div class="tallo"></div>
      <div class="sparkle sparkle-1"></div>
    </div>
    <div class="girasol-container girasol-2 animate">
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="centro"></div>
      <div class="tallo"></div>
      <div class="sparkle sparkle-2"></div>
    </div>
    <div class="girasol-container girasol-3 animate">
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="centro"></div>
      <div class="tallo"></div>
      <div class="sparkle sparkle-3"></div>
    </div>
    <div class="girasol-container girasol-4 animate">
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="centro"></div>
      <div class="tallo"></div>
      <div class="sparkle sparkle-4"></div>
    </div>
    <div class="girasol-container girasol-5 animate">
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="centro"></div>
      <div class="tallo"></div>
      <div class="sparkle sparkle-5"></div>
    </div>
    <div class="girasol-container girasol-6 animate">
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="petalo"></div><div class="petalo"></div><div class="petalo"></div>
      <div class="centro"></div>
      <div class="tallo"></div>
      <div class="sparkle sparkle-6"></div>
    </div>
    <div class="heart heart-1"><div class="heart-shape"></div></div>
    <div class="heart heart-2"><div class="heart-shape"></div></div>
    <div class="heart heart-3"><div class="heart-shape"></div></div>
    <div class="heart heart-4"><div class="heart-shape"></div></div>
    <div class="heart heart-5"><div class="heart-shape"></div></div>
    <div class="heart heart-6"><div class="heart-shape"></div></div>
    <div class="butterfly butterfly-1">
      <div class="wings"></div>
      <div class="body"></div>
      <div class="antenna left"></div>
      <div class="antenna right"></div>
    </div>
    <div class="butterfly butterfly-2">
      <div class="wings"></div>
      <div class="body"></div>
      <div class="antenna left"></div>
      <div class="antenna right"></div>
    </div>
    <div class="butterfly butterfly-3">
      <div class="wings"></div>
      <div class="body"></div>
      <div class="antenna left"></div>
      <div class="antenna right"></div>
    </div>
    <div class="butterfly butterfly-4">
      <div class="wings"></div>
      <div class="body"></div>
      <div class="antenna left"></div>
      <div class="antenna right"></div>
    </div>
  </div>
</body>
</html>
