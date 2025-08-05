<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title> 
Materials Websitec</title>
  <style>
    body {
      background-color: #fff0f5;
      font-family: Arial, sans-serif;
    }
  </style>
</head>
<body>
  <script>
    function startGame() {
      const question = "Hey Jinny 나랑 데이트할래?";
      const yesButton = "좋아";
      const noButton = "아니";

      let isFirstAttempt = true;

      function askQuestion() {
        const dialog = document.createElement("div");
        dialog.style.backgroundColor = "#f0f0f0";
        dialog.style.border = "2px solid #000";
        dialog.style.padding = "20px";
        dialog.style.borderRadius = "10px";
        dialog.style.boxShadow = "0 4px 8px rgba(0, 0, 0, 0.2)";
        dialog.style.textAlign = "center";
        dialog.style.zIndex = "1000";
        dialog.style.width = "200px";
        dialog.style.height = "150px";

        if (isFirstAttempt) {
          dialog.style.position = "fixed";
          dialog.style.top = "50%";
          dialog.style.left = "50%";
          dialog.style.transform = "translate(-50%, -50%)";
          isFirstAttempt = false;
        } else {
          dialog.style.position = "absolute";
          dialog.style.transform = "none";
          const x = Math.random() * (window.innerWidth - 220);
          const y = Math.random() * (window.innerHeight - 170);
          dialog.style.left = `${x}px`;
          dialog.style.top = `${y}px`;
        }

        const questionText = document.createElement("p");
        questionText.textContent = question;
        dialog.appendChild(questionText);

        const yesBtn = document.createElement("button");
        yesBtn.textContent = yesButton;
        yesBtn.style.margin = "10px";
        yesBtn.onclick = () => {
          dialog.remove();
          showHeart();
        };
        dialog.appendChild(yesBtn);

        const noBtn = document.createElement("button");
        noBtn.textContent = noButton;
        noBtn.style.margin = "10px";
        noBtn.onclick = () => {
          dialog.remove();
          showMessage(); // Mostrar mensaje "Nice try!"
          setTimeout(askQuestion, 600); // Esperar antes de mostrar la pregunta de nuevo
        };
        dialog.appendChild(noBtn);

        document.body.appendChild(dialog);
      }

      function showHeart() {
        const heartDialog = document.createElement("div");
        heartDialog.style.position = "fixed";
        heartDialog.style.top = "50%";
        heartDialog.style.left = "50%";
        heartDialog.style.transform = "translate(-50%, -50%)";
        heartDialog.style.backgroundColor = "#ffcccc";
        heartDialog.style.border = "2px solid #ff0000";
        heartDialog.style.padding = "20px";
        heartDialog.style.borderRadius = "10px";
        heartDialog.style.boxShadow = "0 4px 8px rgba(0, 0, 0, 0.2)";
        heartDialog.style.textAlign = "center";
        heartDialog.style.zIndex = "1000";

        const heartText = document.createElement("p");
        heartText.textContent = "Let me get your number❤️";
        heartText.style.fontSize = "50px";
        heartDialog.appendChild(heartText);

        document.body.appendChild(heartDialog);
      }

      function showMessage() {
        const msg = document.createElement("div");
        msg.textContent = "Nice try! Inténtalo de nuevo.";
        msg.style.position = "fixed";
        msg.style.top = "10%";
        msg.style.left = "50%";
        msg.style.transform = "translateX(-50%)";
        msg.style.backgroundColor = "#ffd700";
        msg.style.color = "#000";
        msg.style.padding = "10px 20px";
        msg.style.borderRadius = "10px";
        msg.style.boxShadow = "0 4px 8px rgba(0, 0, 0, 0.2)";
        msg.style.fontWeight = "bold";
        msg.style.zIndex = "2000";

        document.body.appendChild(msg);

        setTimeout(() => {
          msg.remove();
        }, 1000);
      }

      askQuestion();
    }

    window.onload = startGame;
  </script>
</body>
</html>
