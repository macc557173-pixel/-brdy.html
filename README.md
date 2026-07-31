<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Surprise 🎂</title>
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body {
    min-height: 100vh;
    overflow: hidden;
    font-family: Arial, sans-serif;
    background: #080014;
    color: white;
}
/* =========================
   DATE LOCK SCREEN
========================= */
#lockScreen {
    position: fixed;
    inset: 0;
    z-index: 100;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    background:
        radial-gradient(circle at center,
        #49126e 0%,
        #18052c 45%,
        #050008 100%);
}
.lockBox {
    width: min(90%, 450px);
    padding: 45px 30px;
    border-radius: 30px;
    background: rgba(255,255,255,.08);
    border: 1px solid rgba(255,255,255,.2);
    backdrop-filter: blur(20px);
    box-shadow:
        0 0 60px rgba(190,70,255,.4);
    animation: boxFloat 3s ease-in-out infinite;
}
@keyframes boxFloat {
    0%,100% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(-10px);
    }
}
.lockIcon {
    font-size: 65px;
    margin-bottom: 15px;
}
.lockBox h1 {
    font-size: 32px;
    margin-bottom: 12px;
}
.lockBox p {
    color: #ddd;
    margin-bottom: 25px;
    line-height: 1.6;
}
input {
    width: 100%;
    padding: 15px;
    border-radius: 15px;
    border: none;
    outline: none;
    background: rgba(255,255,255,.95);
    color: #222;
    font-size: 17px;
    text-align: center;
}
.unlockBtn {
    margin-top: 18px;
    padding: 15px 35px;
    border: none;
    border-radius: 30px;
    background: linear-gradient(
        90deg,
        #ff42b3,
        #9b5cff
    );
    color: white;
    font-size: 17px;
    font-weight: bold;
    cursor: pointer;
    box-shadow:
        0 0 25px rgba(255,60,190,.5);
    transition: .3s;
}
.unlockBtn:hover {
    transform: scale(1.07);
}
#error {
    margin-top: 15px;
    color: #ff8fbd;
    display: none;
}
/* =========================
   BIRTHDAY PAGE
========================= */
#birthdayPage {
    display: none;
    min-height: 100vh;
    position: relative;
    overflow: hidden;
    background:
        radial-gradient(circle at center,
        #4d176c,
        #15051f 60%,
        #030007);
}
.stars {
    position: absolute;
    inset: 0;
    background-image:
        radial-gradient(white 1px, transparent 1px),
        radial-gradient(white 1px, transparent 1px);
    background-size: 80px 80px, 120px 120px;
    opacity: .4;
    animation: moveStars 20s linear infinite;
}
@keyframes moveStars {
    from {
        transform: translateY(0);
    }
    to {
        transform: translateY(-120px);
    }
}
.content {
    position: relative;
    z-index: 5;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    perspective: 1000px;
}
.subtitle {
    font-size: 18px;
    letter-spacing: 5px;
    text-transform: uppercase;
}
.title {
    margin-top: 15px;
    font-size: clamp(45px, 10vw, 95px);
    font-weight: 900;
    background:
        linear-gradient(
            90deg,
            #fff,
            #ffb5ec,
            #d89cff,
            #fff
        );
    -webkit-background-clip: text;
    color: transparent;
    text-shadow:
        0 0 20px rgba(255,255,255,.4),
        0 0 50px rgba(224,100,255,.6);
    animation: title3d 3s ease-in-out infinite;
}
@keyframes title3d {
    0%,100% {
        transform:
            translateY(0)
            rotateX(0deg);
    }
    50% {
        transform:
            translateY(-15px)
            rotateX(8deg);
    }
}
.personName {
    margin-top: 10px;
    font-size: clamp(28px, 6vw, 55px);
    color: #ffd65a;
    text-shadow:
        0 0 15px #ffd65a,
        0 0 35px rgba(255,214,90,.6);
}
/* =========================
   3D CAKE
========================= */
.cakeScene {
    width: 300px;
    height: 220px;
    margin-top: 10px;
    perspective: 900px;
}
.cake {
    position: relative;
    width: 190px;
    height: 100px;
    margin: 70px auto;
    transform-style: preserve-3d;
    animation:
        cakeRotate 8s linear infinite;
}
@keyframes cakeRotate {
    from {
        transform: rotateY(0deg);
    }
    to {
        transform: rotateY(360deg);
    }
}
.cakeLayer {
    position: absolute;
    width: 190px;
    height: 55px;
    bottom: 0;
    border-radius: 15px;
    background:
        linear-gradient(
            #ff8dcc,
            #c6327e
        );
    border: 3px solid #ffc1e4;
    box-shadow:
        inset 0 -12px 15px rgba(0,0,0,.25),
        0 15px 30px rgba(0,0,0,.4);
}
.topLayer {
    width: 155px;
    height: 50px;
    left: 17px;
    bottom: 45px;
    background:
        linear-gradient(
            #b78aff,
            #7132bd
        );
}
.cream {
    position: absolute;
    width: 190px;
    height: 25px;
    top: 15px;
    border-radius: 50%;
    background: white;
    box-shadow:
        0 0 20px rgba(255,255,255,.7);
}
/* Candles */
.candle {
    position: absolute;
    width: 13px;
    height: 55px;
    top: -55px;
    border-radius: 5px;
    background:
        linear-gradient(
            90deg,
            white,
            #ffd34d,
            white
        );
}
.candle1 {
    left: 55px;
}
.candle2 {
    left: 88px;
}
.candle3 {
    left: 121px;
}
.flame {
    position: absolute;
    width: 15px;
    height: 23px;
    top: -23px;
    background: #ffb300;
    border-radius: 50%;
    box-shadow:
        0 0 20px #ffb300;
    animation:
        flame .4s infinite alternate;
}
@keyframes flame {
    from {
        transform: scale(.8);
    }
    to {
        transform: scale(1.1);
    }
}
/* =========================
   BUTTON
========================= */
.surpriseBtn {
    padding: 15px 32px;
    border: none;
    border-radius: 30px;
    background:
        linear-gradient(
            90deg,
            #ff42b3,
            #8f55ff
        );
    color: white;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
    box-shadow:
        0 0 25px rgba(255,60,190,.6);
}
/* =========================
   BALLOONS
========================= */
.balloon {
    position: absolute;
    width: 65px;
    height: 85px;
    bottom: -120px;
    border-radius: 50%;
    z-index: 3;
    animation:
        balloonUp 12s linear infinite;
}
.balloon::after {
    content: "";
    position: absolute;
    width: 2px;
    height: 120px;
    top: 82px;
    left: 50%;
    background: white;
    opacity: .5;
}
.b1 {
    left: 7%;
    background: #ff4fa8;
}
.b2 {
    left: 25%;
    background: #795cff;
    animation-delay: 3s;
}
.b3 {
    right: 25%;
    background: #ffd34d;
    animation-delay: 1s;
}
.b4 {
    right: 7%;
    background: #42e6c1;
    animation-delay: 4s;
}
@keyframes balloonUp {
    from {
        transform:
            translateY(0)
            rotate(-5deg);
    }
    to {
        transform:
            translateY(-120vh)
            rotate(10deg);
    }
}
/* =========================
   POPUP
========================= */
#popup {
    display: none;
    position: fixed;
    inset: 0;
    z-index: 200;
    justify-content: center;
    align-items: center;
    background: rgba(0,0,0,.7);
    backdrop-filter: blur(8px);
}
.popupBox {
    width: min(90%,500px);
    padding: 40px;
    border-radius: 25px;
    text-align: center;
    background:
        rgba(255,255,255,.1);
    border:
        1px solid rgba(255,255,255,.25);
    box-shadow:
        0 0 60px rgba(220,100,255,.5);
}
.popupBox h2 {
    font-size: 40px;
    color: #ffd65a;
    margin-bottom: 20px;
}
.popupBox p {
    font-size: 18px;
    line-height: 1.7;
}
.closeBtn {
    margin-top: 25px;
    padding: 12px 30px;
    border: none;
    border-radius: 25px;
    background: white;
    color: #40105e;
    font-weight: bold;
}
/* Mobile */
@media(max-width:600px) {
    .lockBox {
        padding: 35px 20px;
    }
    .cakeScene {
        transform: scale(.8);
        margin-top: 0;
    }
    .balloon {
        width: 45px;
        height: 65px;
    }
}
</style>
</head>
<body>
<!-- =========================
     FIRST SCREEN
========================= -->
<section id="lockScreen">
    <div class="lockBox">
        <div class="lockIcon">
            🎁
        </div>
        <h1>
            A Special Surprise
        </h1>
        <p>
            A little surprise is waiting for her... 💜
            <br>
            Enter her birthday date to unlock it.
        </p>
        <!-- Change the date in JavaScript below -->
        <input
            type="date"
            id="birthdayDate"
        >
        <br>
        <button
            class="unlockBtn"
            onclick="unlockBirthday()"
        >
            🔐 Unlock Surprise
        </button>
        <div id="error">
            Hmm... that's not the right date. Try again 💜
        </div>
    </div>
</section>
<!-- =========================
     BIRTHDAY PAGE
========================= -->
<section id="birthdayPage">
    <div class="stars"></div>
    <!-- Balloons -->
    <div class="balloon b1"></div>
    <div class="balloon b2"></div>
    <div class="balloon b3"></div>
    <div class="balloon b4"></div>
    <div class="content">
        <div class="subtitle">
            Today is your special day ✨
        </div>
        <div class="title">
            Happy Birthday
        </div>
        <!-- Change her name here -->
        <div class="personName">
            chunni 💖
        </div>
        <!-- 3D Cake -->
        <div class="cakeScene">
            <div class="cake">
                <div class="cakeLayer"></div>
                <div class="cakeLayer topLayer"></div>
                <div class="cream"></div>
                <div class="candle candle1">
                    <div class="flame"></div>
                </div>
                <div class="candle candle2">
                    <div class="flame"></div>
                </div>
                <div class="candle candle3">
                    <div class="flame"></div>
                </div>
            </div>
        </div>
        <button
            class="surpriseBtn"
            onclick="showMessage()"
        >
            🎁 Open Your Surprise
        </button>
    </div>
</section>
<!-- =========================
     MESSAGE POPUP
========================= -->
<div id="popup">
    <div class="popupBox">
        <h2>
            🎂 Happy Birthday!
        </h2>
        <p>
            May your special day be filled with
            happiness, beautiful memories,
            laughter and wonderful moments. 💖
            <br><br>
            You deserve all the happiness in the world! ✨
        </p>
        <button
            class="closeBtn"
            onclick="closeMessage()"
        >
            Close ❤️
        </button>
    </div>
</div>
<script>
/*
=========================================
IMPORTANT
=========================================
SET HER REAL BIRTHDAY HERE.
Example:
If her birthday is 15 August 2005
write:
const correctBirthday = "2005-08-15";
Format:
YYYY-MM-DD
*/
const correctBirthday = "2006-07-31";
function unlockBirthday() {
    const enteredDate =
        document.getElementById("birthdayDate").value;
    const error =
        document.getElementById("error");
    if (enteredDate === correctBirthday) {
        // Hide lock screen
        document.getElementById("lockScreen").style.display =
            "none";
        // Show birthday page
        document.getElementById("birthdayPage").style.display =
            "block";
        // Start celebration
        createConfetti();
    } else {
        error.style.display = "block";
    }
}
/* Birthday popup */
function showMessage() {
    document.getElementById("popup").style.display =
        "flex";
    createConfetti();
}
function closeMessage() {
    document.getElementById("popup").style.display =
        "none";
}
/* Confetti */
function createConfetti() {
    for (let i = 0; i < 120; i++) {
        const confetti =
            document.createElement("div");
        confetti.style.position = "fixed";
        confetti.style.width = "9px";
        confetti.style.height = "16px";
        confetti.style.left =
            Math.random() * 100 + "vw";
        confetti.style.top = "-30px";
        confetti.style.zIndex = "300";
        confetti.style.background =
            `hsl(${Math.random() * 360}, 90%, 65%)`;
        confetti.style.transform =
            `rotate(${Math.random() * 360}deg)`;
        confetti.style.transition =
            `transform ${2 + Math.random() * 3}s linear,
             top ${2 + Math.random() * 3}s linear`;
        document.body.appendChild(confetti);
        setTimeout(() => {
            confetti.style.top = "110vh";
            confetti.style.transform =
                `rotate(${Math.random() * 1000}deg)`;
        }, 50);
        setTimeout(() => {
            confetti.remove();
        }, 5500);
    }
}
</script>
</body>
</html>