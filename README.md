
# Something-different-and-new

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Do you like me?</title>
  <style>
    body {
      margin: 0; height: 100vh; display: grid; place-items: center;
      background: radial-gradient(circle at 20% 20%, #ffe, #ffd6d6);
      font-family: system-ui, Arial, sans-serif;
    }
    .card {
      width: min(92vw, 480px);
      background: #fff; border-radius: 20px; padding: 28px;
      box-shadow: 0 20px 60px rgba(0,0,0,.12);
      text-align: center; position: relative; overflow: hidden;
    }
    .emojis { font-size: 28px; line-height: 1.6; }
    h1 { margin: 10px 0 8px; font-size: 26px; }
    p { margin: 0 0 18px; font-size: 16px; color: #444; }
    .btns { position: relative; height: 140px; }
    button {
      position: absolute; padding: 12px 20px; border-radius: 999px;
      border: 0; font-weight: 700; cursor: pointer; font-size: 16px;
      box-shadow: 0 10px 24px rgba(0,0,0,.12);
      transition: transform .08s ease;
    }
    #yes { left: 20%; top: 45%; background: #12d06b; color: #fff; }
    #no  { left: 55%; top: 45%; background: #ff4d6d; color: #fff; }
    #msg { display: none; font-size: 18px; margin-top: 10px; }
    .hearts {
      position: absolute; inset: 0; pointer-events: none; opacity: .15;
      font-size: 28px; animation: float 10s linear infinite;
    }
    @keyframes float { from { transform: translateY(20px);} to { transform: translateY(-20px);} }
  </style>
</head>
<body>
  <div class="card" id="card">
    <div class="hearts">❤️ 💖 💘 💞 💗 💓 💝 ❤️ 💖 💘 💞 💗 💓 💝</div>
    <div class="emojis">😁??</div>
    <h1>Do you like me?</h1>
    <p>Socho mat. Bas dil se answer do.</p>

    <div class="btns" id="arena">
      <button id="yes">Yes 😍</button>
      <button id="no">No 🙅‍♀️</button>
    </div>

    <div id="msg">Yay! Thanks <b>and</b> welcome my luxury life😎💖</div>
  </div>

  <script>
    const arena = document.getElementById('arena');
    const noBtn = document.getElementById('no');
    const yesBtn = document.getElementById('yes');
    const msg = document.getElementById('msg');

    function moveNo() {
      const rect = arena.getBoundingClientRect();
      const b = noBtn.getBoundingClientRect();
      const pad = 8;
      const maxX = rect.width  - b.width  - pad;
      const maxY = rect.height - b.height - pad;
      const x = Math.max(pad, Math.random() * maxX);
      const y = Math.max(pad, Math.random() * maxY);
      noBtn.style.left = x + "px";
      noBtn.style.top  = y + "px";
    }

    ["mouseenter","mousemove","focus","touchstart"].forEach(ev =>
      noBtn.addEventListener(ev, e => { moveNo(); e.preventDefault(); })
    );
    noBtn.addEventListener("click", e => { e.preventDefault(); moveNo(); });

    yesBtn.addEventListener("click", () => {
      msg.style.display = "block";
      yesBtn.textContent = "love you too 🌸🫂";
      yesBtn.style.transform = "scale(1.08)";
      setTimeout(()=> yesBtn.style.transform = "scale(1)", 120);
    });

    moveNo(); // initial random position
  </script>
</body>
</html>