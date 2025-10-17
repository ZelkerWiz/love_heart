<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>I ❤️ U</title>
  <style>
    body {
      background-color: black;
      color: white;
      font-family: "Courier New", monospace;
      text-align: center;
      overflow: hidden;
      height: 100vh;
    }

    .typewriter {
      font-size: 1.4rem;
      white-space: pre-line;
      display: inline-block;
    }

    .heart {
      font-size: 24px;
      line-height: 1.2;
      white-space: pre;
      display: inline-block;
      margin: 20px 0;
    }

    .fade {
      animation: fade 1s infinite alternate;
    }

    @keyframes fade {
      from { opacity: 0.7; }
      to { opacity: 1; }
    }
  </style>
</head>
<body>
  <div id="output" class="typewriter"></div>
  <div id="heart" class="heart"></div>

  <script>
    const messages = [
      "ANH THÍCH EM 💖",
      "Anh chúc em có một ngày thật vui vẻ và hạnh phúc nhaa 🌸",
      "Hi vọng em thích món quà này nhee haha 😆",
      "Em sẵn sàng chưa nèee...",
      "3, 2, 1 — BẮT ĐẦU 💞"
    ];

    const frames = [
      
`     ======       ======    
    ==========   ==========  
   ========================== 
 ==============================
  =========================== 
    =======================   
       =================     
         =============      
           =========        
             =====        
              ===           `,
`       ====       ====    
      ========   ========  
    ======================= 
  ===========================
    ======================= 
      ===================   
         =============     
           =========      
             =====        
              ===        
                           `,
`       ===        ===   
      =======    ======= 
     =====================
    =======================
      =================== 
        ===============   
           =========     
             =====      
              ===        
                       
                         `,
`       ====       ====    
      ========   ========  
    ======================= 
  ===========================
    ======================= 
      ===================   
         =============     
           =========      
             =====        
              ===        
                         `,
    ];

    const colors = ["#ff0000", "#ff66cc", "#ff33ff", "#ff5050"];
    let colorIndex = 0;
    let frameIndex = 0;

    async function typeWriter(text, delay = 80) {
      const output = document.getElementById("output");
      for (let i = 0; i < text.length; i++) {
        output.innerHTML += text[i];
        await new Promise(r => setTimeout(r, delay));
      }
      output.innerHTML += "<br>";
      await new Promise(r => setTimeout(r, 1000));
    }

    async function playHeart() {
      const heartEl = document.getElementById("heart");
      while (true) {
        heartEl.style.color = colors[colorIndex];
        heartEl.textContent = frames[frameIndex];
        frameIndex = (frameIndex + 1) % frames.length;
        colorIndex = (colorIndex + 1) % colors.length;
        await new Promise(r => setTimeout(r, 150));
      }
    }

    async function start() {
      for (let msg of messages) {
        await typeWriter(msg);
      }
      document.getElementById("heart").classList.add("fade");
      playHeart();
    }

    start();
  </script>
</body>
</html>
