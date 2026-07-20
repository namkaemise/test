<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>나를 죽이려는 SSS급 킬러의 상태창이 보인다</title>

<link href="https://fonts.googleapis.com/css2?family=Diphylleia&family=Nanum+Pen+Script&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box;}

body{
    font-family:'Noto Sans KR',sans-serif;
    background:	#000000;
    color:#6495ED;
    overflow-x:hidden;
}

/* 노이즈 */
body::before{
    content:"";
    position:fixed;
    inset:0;
    background:url("(https://raw.githubusercontent.com/namkaemise/RyuJaemin/refs/heads/main/Unknown.jpeg)");
    opacity:0.04;
    pointer-events:none;
}

/* 파티클 */
.particles{
    position:fixed;
    inset:0;
    pointer-events:none;
}
.particles span{
    position:absolute;
    width:3px;height:3px;
    background:white;
    border-radius:50%;
    opacity:0.15;
    animation:float 20s linear infinite;
}
@keyframes float{
    from{transform:translateY(100vh);}
    to{transform:translateY(-10vh);}
}

/* 상단 메뉴 */
.top-menu{
    position:fixed;
    top:0;width:100%;
    display:flex;
    justify-content:center;
    gap:20px;
    padding:20px;
    background:rgba(0,0,0,0.3);
    backdrop-filter:blur(10px);
}
.menu-btn{
    padding:10px 25px;
    border-radius:30px;
    border:1px solid rgba(168,85,247,0.4);
    background:transparent;
    color:	#0000CD;
    cursor:pointer;
    font-family:'Orbitron',sans-serif;
}
.menu-btn.active,
.menu-btn:hover{
    background:linear-gradient(45deg,	#000000,#0000CD);
    color:white;
}

/* 섹션 */
.section{
    min-height:100vh;
    display:none;
    padding:140px 20px 80px;
    text-align:center;
}
.section.active{display:block;}

h1,h2{
    font-family:'Orbitron',sans-serif;
    letter-spacing:1px;
}
h1{
    font-size:2.3rem;
    color: white;
    text-shadow:0 0 255px rgba(168,85,247,0.6);
}

/* Information */
.character-img{
    width:240px;
    aspect-ratio:3:4;
    object-fit:cover;
    border-radius:20px;
    margin-bottom:20px;
    box-shadow:0 0 255px rgba(168,85,247,0.5);
}
.world-desc{
    max-width:600px;
    margin:20px auto;
    font-weight:300;
    line-height:1.6;
    opacity:0.8;
}
.chat-box{
    max-width:600px;
    margin:30px auto;
    padding:30px;
    border-radius:20px;
    backdrop-filter:blur(12px);
    background:rgba(255,255,255,0.05);
    border:1px solid rgba(192,132,252,0.2);
}
.play-btn{
    margin-top:50px;
    padding:22px 70px;
    font-size:1.6rem;
    border:none;
    border-radius:50px;
    background:linear-gradient(45deg,	#6495ED,#0000CD);
    color:white;
    cursor:pointer;
    font-family:'Orbitron',sans-serif;
    box-shadow:0 0 255px rgba(168,85,247,0.6);
}

/* Gallery */
.gallery-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
    gap:20px;
    max-width:900px;
    margin:0 auto;
}
.gallery-grid img{
    width:100%;
    border-radius:15px;
    cursor:pointer;
    transition:0.3s;
    box-shadow:0 0 255px rgba(168,85,247,0.2);
}
.gallery-grid img:hover{
    transform:scale(1.05);
    box-shadow:0 0 255px rgba(168,85,247,0.6);
}

/* 모달 */
.modal{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,0.8);
    backdrop-filter:blur(10px);
    display:flex;
    justify-content:center;
    align-items:center;
    opacity:0;
    pointer-events:none;
    transition:0.3s;
}
.modal.active{
    opacity:1;
    pointer-events:all;
}
.modal img{
    max-width:80%;
    max-height:80%;
    border-radius:20px;
    box-shadow:0 0 255px rgba(168,85,247,0.7);
}

/* OST */
.music-panel{
    max-width:500px;
    margin:0 auto;
    padding:40px;
    border-radius:25px;
    background:rgba(255,255,255,0.05);
    backdrop-filter:blur(15px);
    border:1px solid rgba(192,132,252,0.2);
    box-shadow:0 0 255px rgba(168,85,247,0.3);
}
.track-title{
    font-family:'Orbitron',sans-serif;
    font-size:1.2rem;
    color:white;
}
.music-controls button{
    width:40px;
    height:40px;
    border-radius:50%;
    border:none;
    font-size:1.2rem;
    cursor:pointer;
    background:linear-gradient(45deg,	#000000,#6495ED);
    color:white;
    box-shadow:0 0 255px rgba(168,85,247,0.6);
}
.wave{
    margin-top:30px;
    height:4px;
    background:linear-gradient(to right,	#000000,#6495ED);
    animation:waveAnim 1.2s infinite ease-in-out;
    opacity:0.5;
}
@keyframes waveAnim{
    0%{transform:scaleX(0.6);}
    50%{transform:scaleX(1);}
    100%{transform:scaleX(0.6);}
}

/* 로딩 */
#loading-screen{
    position:fixed;inset:0;
    background:	white;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    opacity:0;
    pointer-events:none;
    transition:0.4s;
}
#loading-screen.active{
    opacity:1;
    pointer-events:all;
}
.loader{
    width:60px;height:60px;
    border:5px solid rgba(255,255,255,0.1);
    border-top:5px solid 	white;
    border-radius:50%;
    animation:spin 1s linear infinite;
}
@keyframes spin{to{transform:rotate(360deg);}}
</style>
</head>

<body>

<div class="particles"></div>

<div class="top-menu">
    <button class="menu-btn active" onclick="showSection('intro',this)">Intro</button>
    <button class="menu-btn" onclick="showSection('gallery',this)">Gallery</button>
    <button class="menu-btn" onclick="showSection('music',this)">OST</button>
</div>

<section id="intro" class="section active">
    <img src="IMG_6111.jpeg" class="character-img">
    <h1>류재민</h1>
    <div class="world-desc">SSS급 킬러와의 전투. 이미 승패는 결정되었다. 허벅지를 관통한 총상, 멈추지 않는 출혈. 그리고 이마를 겨누는 총구.
        죽음을 받아들이려던 순간, 절대 패배하지 않을 것 같던 괴물이 갑자기 무릎을 꿇었다.
        원인 불명의 상태이상.
        그리고 눈앞에 떠오른 의문의 시스템.</div>
    
    <div class="chat-box">
        『⚠ 상태이상 : 음란마귀』
        
        『미션 : 남의 손으로 가버리기♥』</div>
    
    <div class="world-desc">살아남으려면, 이 미친 미션을 수행해야 한다.
최악의 상태이상과 함께 시작되는, 가장 위험하고도 수치스러운 생존 이야기.</div>
    <button class="play-btn" onclick="startLoading()">▶ Play</button>
</section>

<section id="gallery" class="section">
    <h2 style="color:	white;margin-bottom:40px;">GALLERY</h2>
    <div class="gallery-grid">
        <img src="IMG_5990.webp" onclick="openModal(this.src)">
        <img src="IMG_5999.webp" onclick="openModal(this.src)">
        <img src="IMG_6044.webp" onclick="openModal(this.src)">
        <img src="IMG_6052.webp" onclick="openModal(this.src)">
        <img src="IMG_6047.webp" onclick="openModal(this.src)">
    </div>
</section>

<section id="music" class="section">
    <h2 style="color:		white;margin-bottom:40px;">ORIGINAL SOUND TRACK</h2>
    <div class="music-panel">
        <div class="track-title">Character Theme</div>
        <div class="music-controls">
            <button onclick="toggleMusic()" id="playBtn">▶</button>
        </div>
        <div class="wave"></div>
    </div>
    <audio id="bgm" src="Vixx Chained Up ( (Chained Up)).mp3"></audio>
</section>

<div id="modal" class="modal" onclick="closeModal()">
    <img id="modalImg">
</div>

<div id="loading-screen">
    <div class="loader"></div>
    <div style="margin-top:20px;">CONNECTING...</div>
</div>

<script>
const p=document.querySelector(".particles");
for(let i=0;i<35;i++){
    const s=document.createElement("span");
    s.style.left=Math.random()*100+"%";
    s.style.animationDuration=(15+Math.random()*10)+"s";
    p.appendChild(s);
}

function showSection(id,btn){
    document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"));
    document.getElementById(id).classList.add("active");
    document.querySelectorAll(".menu-btn").forEach(b=>b.classList.remove("active"));
    btn.classList.add("active");
}

function openModal(src){
    document.getElementById("modalImg").src=src;
    document.getElementById("modal").classList.add("active");
}
function closeModal(){
    document.getElementById("modal").classList.remove("active");
}

function toggleMusic(){
    const audio=document.getElementById("bgm");
    const btn=document.getElementById("playBtn");
    if(audio.paused){
        audio.play();
        btn.textContent="❚❚";
    }else{
        audio.pause();
        btn.textContent="▶";
    }
}

function startLoading(){
    const l=document.getElementById("loading-screen");
    l.classList.add("active");
    setTimeout(()=>{
        window.location.href="https://share.crack.wrtn.ai/g5sojd";
    },2500);
}
</script>

</body>
</html>
