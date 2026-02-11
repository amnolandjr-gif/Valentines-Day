<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>💕 Will You Be My Valentine? 💕</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', sans-serif;
      overflow-x: hidden;
    }

    #app {
      min-height: 100vh;
      background: linear-gradient(to bottom right, #fce7f3, #fee2e2, #fce7f3);
      padding: 2rem;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .container {
      text-align: center;
      max-width: 48rem;
      width: 100%;
    }

    .hearts-top {
      margin-bottom: 2rem;
      font-size: 3rem;
    }

    h1 {
      font-size: 3.75rem;
      font-weight: bold;
      color: #db2777;
      margin-bottom: 2rem;
    }

    .message-box {
      background: white;
      padding: 1.5rem;
      border-radius: 1rem;
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
      margin-bottom: 2rem;
      border: 2px solid #f9a8d4;
      animation: shake 0.5s ease-in-out;
    }

    .message-box p {
      font-size: 1.5rem;
      color: #374151;
      font-weight: 500;
    }

    .progress-box {
      background: white;
      padding: 1rem;
      border-radius: 0.75rem;
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
      margin-bottom: 2rem;
      border: 2px solid #86efac;
    }

    .progress-box p {
      font-size: 1.25rem;
      color: #374151;
      font-weight: 500;
    }

    .button-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 2rem;
      margin-top: 3rem;
    }

    .yes-button {
      background: #22c55e;
      color: white;
      font-weight: bold;
      border-radius: 9999px;
      border: none;
      cursor: pointer;
      box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
      transition: all 0.3s;
    }

    .yes-button:hover {
      background: #16a34a;
      transform: scale(1.05);
    }

    .no-button {
      background: #ef4444;
      color: white;
      font-weight: bold;
      padding: 1rem 3rem;
      border-radius: 9999px;
      font-size: 1.5rem;
      border: none;
      cursor: pointer;
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
      transition: all 0.3s;
    }

    .no-button:hover {
      background: #dc2626;
    }

    .hint-text {
      color: #4b5563;
      margin-top: 3rem;
      font-size: 1.125rem;
      font-style: italic;
    }

    .explosion-screen {
      min-height: 100vh;
      background: linear-gradient(to bottom right, #fbcfe8, #fecaca, #fbcfe8);
      padding: 2rem;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .explosion-container {
      text-align: center;
      position: relative;
    }

    .explosion-hearts {
      position: relative;
      height: 200px;
      margin-bottom: 2rem;
    }

    .explosion-heart {
      position: absolute;
      font-size: 3rem;
      left: 50%;
      top: 50%;
      animation: float 2s ease-out infinite;
    }

    .celebration-box {
      background: white;
      padding: 3rem;
      border-radius: 1.5rem;
      box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
      max-width: 42rem;
      border: 4px solid #f9a8d4;
      position: relative;
      z-index: 10;
    }

    .celebration-emoji {
      font-size: 5rem;
      margin-bottom: 1.5rem;
    }

    .celebration-title {
      font-size: 3rem;
      font-weight: bold;
      color: #db2777;
      margin-bottom: 1.5rem;
    }

    .celebration-subtitle {
      font-size: 1.875rem;
      color: #1f2937;
      margin-bottom: 2rem;
      font-weight: 500;
    }

    .dinner-details {
      background: linear-gradient(to right, #fce7f3, #fee2e2);
      padding: 2rem;
      border-radius: 1rem;
      margin-bottom: 1.5rem;
    }

    .dinner-title {
      font-size: 1.5rem;
      color: #1f2937;
      margin-bottom: 1rem;
      font-weight: 600;
    }

    .dinner-info {
      font-size: 1.25rem;
      color: #374151;
    }

    .dinner-info p {
      font-weight: 500;
      margin-bottom: 0.75rem;
    }

    .celebration-text {
      font-size: 1.25rem;
      color: #4b5563;
      margin-bottom: 1rem;
    }

    .celebration-hearts {
      font-size: 3rem;
      margin-top: 2rem;
    }

    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-10px); }
      75% { transform: translateX(10px); }
    }

    @keyframes float {
      0% { 
        opacity: 1; 
        transform: translate(-50%, -50%) translateY(0) scale(1); 
      }
      100% { 
        opacity: 0; 
        transform: translate(-50%, -50%) translateY(-200px) scale(1.5); 
      }
    }

    @media (max-width: 640px) {
      h1 { font-size: 2.5rem; }
      .message-box p { font-size: 1.25rem; }
      .celebration-title { font-size: 2rem; }
      .celebration-subtitle { font-size: 1.5rem; }
    }
  </style>
</head>

<body>
  <div id="app"></div>

  <script>
    let noClickCount = 0;
    let yesClickCount = 0;
    let buttonSize = 1;
    let exploded = false;

    const noMessages = [
      "Are you sure? 🥺",
      "Really? Not even a little bit? 💔",
      "But... but... I made this whole game! 😢",
      "What if I said please? Pretty please? 🙏",
      "The Yes button is looking really good though... 👀",
      "I'll even let you pick the dessert! 🍰",
      "Come on, you know you want to click Yes 😏",
      "I'm running out of funny messages here... 😅",
      "The No button is a trick button anyway! 🎭",
      "Fine, I'll just keep asking forever! 😤",
      "Last chance before I start singing... 🎤",
      "Okay seriously, just click Yes already! 😂"
    ];

    function handleNoClick() {
      noClickCount++;
      buttonSize += 0.3;
      render();
    }

    function handleYesClick() {
      yesClickCount++;
      buttonSize += 0.5;
      if (yesClickCount >= 5) exploded = true;
      render();
    }

    function render() {
      const app = document.getElementById('app');

      if (exploded) {
        let explosionHeartsHTML = '';
        for (let i = 0; i < 12; i++) {
          const rotation = i * 30;
          const delay = i * 0.1;
          explosionHeartsHTML += `
            <div class="explosion-heart" style="
              transform: translate(-50%, -50%) rotate(${rotation}deg) translateY(-100px);
              animation-delay: ${delay}s;
            ">❤️</div>
          `;
        }

        app.innerHTML = `
          <div class="explosion-screen">
            <div class="explosion-container">
              <div class="explosion-hearts">${explosionHeartsHTML}</div>
              <div class="celebration-box">
                <div class="celebration-emoji">🎉</div>
                <h1 class="celebration-title">YES!!!</h1>
                <p class="celebration-subtitle">You just made my day! 💕</p>
                <div class="dinner-details">
                  <p class="dinner-title">🍽️ Dinner Date! 🍽️</p>
                  <div class="dinner-info">
                    <p>📍 Estiatorio Plaka</p>
                    <p>📅 Saturday</p>
                    <p>🕖 7:00 PM</p>
                  </div>
                </div>
                <p class="celebration-text">Get ready for an amazing evening! ✨</p>
                <div class="celebration-hearts">💖 💝 💕 💗 💖</div>
              </div>
            </div>
          </div>
        `;
      } else {
        const messageBox = noClickCount > 0 ? `
          <div class="message-box">
            <p>${noMessages[Math.min(noClickCount - 1, noMessages.length - 1)]}</p>
          </div>
        ` : '';

        const progressBox = (yesClickCount > 0 && yesClickCount < 5) ? `
          <div class="progress-box">
            <p>Keep clicking! ${5 - yesClickCount} more time${5 - yesClickCount > 1 ? 's' : ''}! 🎯</p>
          </div>
        ` : '';

        const noButtonMarginLeft = noClickCount * 20;
        const noButtonMarginTop = noClickCount % 2 === 0 ? 0 : -20;

        app.innerHTML = `
          <div class="container">
            <div class="hearts-top">❤️ 💕 ❤️</div>
            <h1>Will you be my Valentine? 💕</h1>
            ${messageBox}
            ${progressBox}
            <div class="button-container">
              <button class="yes-button" onclick="handleYesClick()" style="
                font-size: ${buttonSize * 1.5}rem;
                padding: ${buttonSize * 1}rem ${buttonSize * 2}rem;
                transform: scale(${buttonSize});
              ">
                Yes! 💚
              </button>
              <button class="no-button" onclick="handleNoClick()" style="
                margin-left: ${noButtonMarginLeft}px;
                margin-top: ${noButtonMarginTop}px;
              ">
                No 💔
              </button>
            </div>
            <p class="hint-text">
              ${yesClickCount > 0 ? "That's it! Keep going! 🎉" : "Choose wisely... 😉"}
            </p>
          </div>
        `;
      }
    }

    render();
  </script>
</body>
</html>