<!doctype html>
<html lang="vi">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Just for You 💖</title>
  <style>
    body {
      margin: 0;
      background: #000;
      color: #fff;
      font-family: 'Courier New', monospace;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      min-height: 100vh;
      overflow-x: hidden;
      user-select: none;
    }
    .typewriter {
      font-size: 4vw;
      text-align: center;
      margin: 5vh 10px;
      white-space: pre-wrap;
    }
    pre {
      font-size: 3.5vw;
      line-height: 1.1;
      white-space: pre;
      text-align: center;
      color: #ff4b4b;
      transition: color 0.3s;
      overflow-x: hidden;
      background: #000;      
      border-radius: 10px; 
      text-shadow: 0 0 10px #ff4b4b, 0 0 20px #ff4b4b;
      background-color: #000 !important;
    }
    .c-red { color: #ff4b4b; }
    .c-pink { color: #ff9ddf; }
    .c-purple { color: #d78bff; }

    @media (min-width: 600px) {
      .typewriter { font-size: 20px; }
      pre { font-size: 18px; }
    }
  </style>
</head>
<body>
  <div class="typewriter" id="type"></div>
  <pre id="display" class="c-red"></pre>

  <script>
    const chuI = [
      "==========","==========","   ====   ","   ====   ",
      "   ====   ","   ====   ","   ====   ",
      "   ====   ","==========","=========="
    ];
    const chuU = [
      "===    ===","===    ===","===    ===","===    ===",
      "===    ===","===    ===","===    ===",
      "===    ===","==========","=========="
    ];

    const tim = [
      [
        "     ===     ===    ",
        "   ======   ======  ",
        "  ================= ",
        " ===================",
        "  ================= ",
        "    =============   ",
        "      =========     ",
        "       =======      ",
        "         ===        ",
        "          =         "
      ],
      [
        "      ==     ==    ",
        "    =====   =====  ",
        "   =============== ",
        "  =================",
        "   =============== ",
        "     ===========   ",
        "       =======     ",
        "        =====      ",
        "          =        ",
        "                   "
      ],
      [
        "                  ",
        "     ====   ====  ",
        "    ============= ",
        "   ===============",
        "    ============= ",
        "      =========   ",
        "        =====     ",
        "         ===      ",
        "                  ",
        "                  "
      ],
      [
        "                  ",
        "      ===   ===   ",
        "     ===========  ",
        "    ============= ",
        "     ===========  ",
        "       ========   ",
        "         ===      ",
        "          =       ",
        "                  ",
        "                  "
      ],
      [
        "                  ",
        "       ==   ==    ",
        "      =========   ",
        "     ===========  ",
        "      =========   ",
        "        =====     ",
        "          =       ",
        "                  ",
        "                  ",
        "                  "
      ],
      [
        "                  ",
        "      ===   ===   ",
        "     ===========  ",
        "    ============= ",
        "     ===========  ",
        "       ========   ",
        "         ===      ",
        "          =       ",
        "                  ",
        "                  "
      ],
      [
        "                  ",
        "     ====   ====  ",
        "    ============= ",
        "   ===============",
        "    ============= ",
        "      =========   ",
        "        =====     ",
        "         ===      ",
        "          =       ",
        "                  "
      ],
      [
        "      ==     ==    ",
        "    =====   =====  ",
        "   =============== ",
        "  =================",
        "   =============== ",
        "     ===========   ",
        "       =======     ",
        "        =====      ",
        "          =        ",
        "                   "
      ],
      [
        "     ===     ===    ",
        "   ======   ======  ",
        "  ================= ",
        " ===================",
        "  ================= ",
        "    =============   ",
        "      =========     ",
        "       =======      ",
        "         ===        ",
        "          =         "
      ]
    ];

    const colors = ['c-red','c-pink','c-purple'];
    const display = document.getElementById('display');
    const typeEl = document.getElementById('type');

    const textLines = [
      "just for U",
      "chúc bé có một ngày thật vui vẻ và hạnh phúc nhaa",
      "Hi vọng bé thích món quà này nhee haha",
      "bé sẵn sàng chưa nèe",
      "3, 2, 1, nè!"
    ];

    // Gõ từng dòng kiểu typewriter
    async function typeWriter(text, speed = 70) {
      typeEl.textContent = "";
      for (let c of text) {
        typeEl.textContent += c;
        await new Promise(r => setTimeout(r, speed));
      }
      await new Promise(r => setTimeout(r, 1000));
    }

    function render(frame, color) {
      let output = "";
      for (let i = 0; i < 10; i++) {
        output += chuI[i] + "  " + frame[i] + "    " + chuU[i] + "\n";
      }
      display.className = color;
      display.textContent = output;
    }

    async function start() {
      for (let line of textLines) {
        await typeWriter(line, 80);
      }
      animateHeart();
    }

    function animateHeart() {
      let colorIndex = 0;
      let seq = [...Array(tim.length).keys()];
      let rev = [...seq].slice(0, tim.length - 2).reverse();
      let frames = seq.concat(rev);
      let pos = 0;
      setInterval(() => {
        render(tim[frames[pos]], colors[colorIndex]);
        pos++;
        if (pos >= frames.length) {
          pos = 0;
          colorIndex = (colorIndex + 1) % colors.length;
        }
      }, 100);
    }

    start();
  </script>
</body>
</html>
