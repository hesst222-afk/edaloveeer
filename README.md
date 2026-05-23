<!DOCTYPE html>
<html lang="da">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Til Eda❤️</title>

<style>
    body{
        font-family: Arial, sans-serif;
        background: linear-gradient(to bottom right, #ffb6c1, #ffe4e1);
        text-align:center;
        padding:40px;
        color:#333;
    }

    .container{
        background:white;
        padding:30px;
        border-radius:20px;
        max-width:600px;
        margin:auto;
        box-shadow:0 0 20px rgba(0,0,0,0.2);
    }

    h1{
        color:#ff4d6d;
    }

    input{
        padding:10px;
        border-radius:10px;
        border:1px solid #ccc;
        width:70%;
        margin:5px;
    }

    button{
        margin-top:15px;
        padding:10px 20px;
        border:none;
        border-radius:10px;
        background:#ff4d6d;
        color:white;
        font-size:16px;
        cursor:pointer;
    }

    #game{
        display:none;
        margin-top:20px;
    }

    #board{
        position:relative;
        height:250px;
        border:2px dashed #ff4d6d;
        border-radius:15px;
        overflow:hidden;
    }

    #message{
        display:none;
        margin-top:20px;
        font-size:18px;
        color:#d6336c;
    }

    .heart{
        font-size:50px;
    }
</style>
</head>

<body>

<div class="container">

<h1>Til Eda ❤️</h1>

<!-- 💖 QUIZ -->
<h3>1. Hvem sagde jeg elsker dig først?</h3>
<input id="q1">

<h3>2. Hvor lang tid har vi kendt hinanden?</h3>
<input id="q2">

<button onclick="checkQuiz()">Start spil</button>

<!-- 🎮 SPIL -->
<div id="game">
    <h3>🎮 Fang 10 hjerter</h3>
    <p id="score">Score: 0</p>

    <div id="board"></div>
</div>

<!-- 💌 BESKED -->
<div id="message">
    <h2>💌 Hemmelig besked</h2>

    <p>
        Du betyder alt for mig. Hver dag med dig gør mit liv bedre. Jeg kan ikke forstille mit liv uden dig fordi uden dig så er jeg intet og du må ikke være sur mig på længere. Du er mit alt og jeg mener det, måske siger jeg ikke det tit men du er den eneste jeg tænker på hver eneste sekund. Du den eneste der kan få mig til smile som en idiot. UNDSKYLD for alt de onde ting jeg har sagt og gjort❤️<br><br>

        Jeg elsker dig mere end ord kan beskrive ❤️
    </p>
</div>

</div>

<!-- 🎵 MUSIK -->
<audio autoplay loop>
    <source src="https://s3.ustatik.com/audio.com.audio/source/28/99/1826304024769928-1826304024831155.mp3?response-content-disposition=attachment%3B%20filename%3D%22Drake%20-%20Yebbas%20Heartbreak%20Audio.mp3%22&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=F0E8U41NBMMW3Y027UTJ%2F20260523%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Date=20260523T214424Z&X-Amz-SignedHeaders=host&X-Amz-Expires=518400&X-Amz-Signature=79e7297a8fed954a5b66b1204b31e4a592ed931503f8f32c9ba4c48a543a04f5$0" type="audio/mpeg">
</audio>

<script>

let score = 0;
let quizOK = false;
let gameStarted = false;

// 💖 QUIZ
function checkQuiz(){

    let a1 = document.getElementById("q1").value.toLowerCase().trim();
    let a2 = document.getElementById("q2").value.toLowerCase().trim();

    if(a1 === "eda" && a2 === "2 år"){

        quizOK = true;

        alert("Quiz bestået ❤️ Nu spil!");

        document.getElementById("game").style.display = "block";

        if(!gameStarted){
            setInterval(spawnHeart, 800);
            gameStarted = true;
        }

    } else {
        alert("Forkert svar ❤️");
    }
}

// 🎮 SPIL
function spawnHeart(){

    if(!quizOK) return;
    if(score >= 10) return; // stop når vundet

    let board = document.getElementById("board");

    let heart = document.createElement("div");
    heart.innerHTML = "❤️";
    heart.style.position = "absolute";
    heart.style.fontSize = "30px";
    heart.style.cursor = "pointer";

    heart.style.left = Math.random() * 90 + "%";
    heart.style.top = Math.random() * 80 + "%";

    heart.onclick = function(){

        score++;
        document.getElementById("score").innerText = "Score: " + score;

        heart.remove();

        if(score >= 10){
            document.getElementById("message").style.display = "block";
        }
    }

    board.appendChild(heart);

    setTimeout(() => {
        heart.remove();
    }, 1500);
}

</script>

</body>
</html>
