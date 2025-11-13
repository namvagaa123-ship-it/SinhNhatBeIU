<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Game Sinh Nhật Bé Yêu</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body{
            margin:0;
            display:flex;
            justify-content:center;
            align-items:center;
            min-height:100vh;
            font-family:"Comic Sans MS", Arial, sans-serif;
            background:linear-gradient(135deg,#ffe6f0,#fff0f5);
            overflow:hidden;
        }
        #game-container{
            position:relative;
            width:90vw;
            max-width:500px;
            height:72vw;
            max-height:400px;
        }
        #game{
            width:100%;
            height:100%;
            background:#fff;
            border:3px solid #ff66b2;
            border-radius:15px;
            position:relative;
            overflow:hidden;
            box-shadow:0 0 20px rgba(255,102,178,0.6);
        }
        #player{
            width:12%;
            height:12%;
            position:absolute;
            bottom:10%;
            left:4%;
            z-index:2;
            border-radius:50%;
            overflow:hidden;
            box-shadow:0 4px 8px rgba(0,0,0,0.3);
            transition: top 0.1s, left 0.1s;
        }
        #player img {
            width:100%;
            height:100%;
            object-fit:cover;
        }
        #gift{
            width:12%;
            height:12%;
            border-radius:10px;
            background:#ffcc00;
            position:absolute;
            display:none;
            box-shadow:0 0 10px #ffcc00;
        }
        .obstacle{
            width:12%;
            height:12%;
            position:absolute;
            display:flex;
            justify-content:center;
            align-items:center;
        }
        .cake-base{
            width:80%;
            height:60%;
            background:linear-gradient(to top,#ff99cc,#ff66b2);
            border-radius:6px 6px 8px 8px;
            position:relative;
            box-shadow:0 2px 4px rgba(0,0,0,0.3);
        }
        .icing{
            width:100%;
            height:15%;
            background:#fff0f5;
            border-radius:50%;
            position:absolute;
            top:-2px;
            left:0;
        }
        .candle{
            width:10%;
            height:20%;
            background:yellow;
            border-radius:2px;
            position:absolute;
            top:-25%;
            left:40%;
            box-shadow:0 -10px 0 orange;
            animation:flicker 0.5s infinite alternate;
        }
        @keyframes flicker{
            0%{transform:scaleY(1);opacity:1;}
            50%{transform:scaleY(1.3);opacity:0.8;}
            100%{transform:scaleY(0.9);opacity:1;}
        }
        .heart{
            position:absolute;
            font-size:24px;
            animation:floatUp 2s linear forwards;
        }
        @keyframes floatUp{
            0%{opacity:1; transform:translate(0,0) rotate(0deg);}
            100%{opacity:0; transform:translate(var(--x,0px),-80px) rotate(360deg);}
        }
        #score{
            text-align:center;
            color:#ff3399;
            font-size:5vw;
            margin-top:5px;
        }
        #message{
            text-align:center;
            color:#ff3399;
            font-size:5vw;
            font-weight:bold;
            display:none;
            margin-top:5px;
            line-height:1.5;
        }
        #hitText{
            position:absolute;
            top:45%;
            left:50%;
            transform:translate(-50%,-50%);
            background:rgba(255,255,255,0.8);
            border:2px solid #ff66b2;
            border-radius:10px;
            padding:10px 20px;
            color:#ff0066;
            font-size:4vw;
            font-weight:bold;
            text-align:center;
            display:none;
            box-shadow:0 0 10px rgba(255,102,178,0.4);
        }
        /* Menu Overlay */
        #menu{
            position:absolute;
            top:0;
            left:0;
            width:100%;
            height:100%;
            background:rgba(255,182,193,0.9);
            display:flex;
            flex-direction:column;
            justify-content:center;
            align-items:center;
            z-index:10;
            border-radius:15px;
        }
        #menu h1{
            color:#ff0066;
            font-size:7vw;
            margin-bottom:20px;
            text-shadow: 2px 2px #fff;
            text-align:center;
        }
        .menu-btn{
            background:#ff66b2;
            border:none;
            color:white;
            padding:10px 25px;
            margin:10px;
            font-size:5vw;
            border-radius:10px;
            cursor:pointer;
            box-shadow:0 4px 8px rgba(0,0,0,0.3);
            transition:transform 0.2s;
        }
        .menu-btn:hover{
            transform:scale(1.1);
        }
        /* Control Buttons Mobile */
        #controls{
            position:absolute;
            bottom:5px;
            left:50%;
            transform:translateX(-50%);
            display:flex;
            gap:10px;
            z-index:20;
        }
        .ctrl-btn{
            width:15vw;
            height:15vw;
            max-width:70px;
            max-height:70px;
            background:#ff66b2;
            border-radius:50%;
            color:white;
            font-size:5vw;
            display:flex;
            justify-content:center;
            align-items:center;
            user-select:none;
            touch-action: none;
        }
    </style>
</head>
<body>

<div id="game-container">
    <div id="game">
        <div id="player">
            <img src="https://scontent.fsgn2-11.fna.fbcdn.net/v/t39.30808-1/481810433_683428694012345_3524377575798404095_n.jpg?stp=dst-jpg_s200x200_tt6&_nc_cat=105&ccb=1-7&_nc_sid=e99d92&_nc_eui2=AeHGYOtg_I3pe6ljZ33xku-FGoSKK2jhKXUahIoraOEpdbfrM0iUOAuMXFemYIWeYBrSbYHY0GqIZq4J5LhaOWUF&_nc_ohc=H3SDREIjQJ8Q7kNvwGpihZA&_nc_oc=AdmraKxOUtxcQeUMBvhTML8M-pohQJHaE2-lOtrmCNbYmvIEUfwRZDK8FcTTIw1l0YEFpujqD4ZNdkiPB7WINpQ-&_nc_zt=24&_nc_ht=scontent.fsgn2-11.fna&_nc_gid=0Nx6J-vDqofnbMt5N5Iwxg&oh=00_AfgNQi4YFvNQK_Tarnlsurdcube8Ncs260jlVkLK6SbuJg&oe=691AB483" alt="Nhân vật Bé Yêu">
        </div>
        <div id="gift"></div>
        <div id="hitText">Ôi bé iu bị bánh kem đập mặt :((</div>
    </div>
    <div id="score">Màn: 1</div>
    <div id="message">💖 Chúc mừng bé iu tuổi 22 rực rỡ 💖<br>Mai xinh đẹp, vui vẻ, hạnh phúc, mạnh khỏe 💕</div>
    <div id="menu">
        <h1>🎉 Sinh Nhật Bé Yêu 🎂</h1>
        <button class="menu-btn" id="startBtn">Bắt Đầu</button>
        <button class="menu-btn" id="exitBtn">Thoát</button>
    </div>
    <!-- Nút điều khiển cảm ứng -->
    <div id="controls">
        <div class="ctrl-btn" id="up">↑</div>
        <div class="ctrl-btn" id="left">←</div>
        <div class="ctrl-btn" id="down">↓</div>
        <div class="ctrl-btn" id="right">→</div>
    </div>
</div>

<script>
    // Game logic giữ nguyên như bản desktop
    const player=document.getElementById("player");
    const gift=document.getElementById("gift");
    const game=document.getElementById("game");
    const scoreDisplay=document.getElementById("score");
    const message=document.getElementById("message");
    const hitText=document.getElementById("hitText");

    let playerPos={top:350,left:20};
    const step=10;
    let currentLevel=0;
    let safeZone=false;
    let obstacles=[];

    const gameWidth = game.offsetWidth;
    const gameHeight = game.offsetHeight;

    const levels=[
        {gift:{top:20,left:420}, obstacles:[{top:200,left:100,direction:'down',speed:2},{top:150,left:300,direction:'up',speed:1.5}]},
        {gift:{top:50,left:420}, obstacles:[{top:100,left:150,direction:'down',speed:2.5},{top:250,left:300,direction:'up',speed:2}]},
        {gift:{top:20,left:420}, obstacles:[{top:50,left:50,direction:'right',speed:3},{top:100,left:300,direction:'down',speed:2.5},{top:250,left:100,direction:'up',speed:2.2},{top:300,left:350,direction:'left',speed:2.8}]},
        {gift:{top:20,left:420}, obstacles:[{top:50,left:100,direction:'down',speed:2.5},{top:150,left:200,direction:'right',speed:3},{top:200,left:50,direction:'up',speed:2.7},{top:300,left:300,direction:'left',speed:3},{top:250,left:350,direction:'down',speed:2.3}]},
        {gift:{top:20,left:420}, obstacles:[{top:50,left:50,direction:'right',speed:3.2},{top:150,left:250,direction:'left',speed:2.8},{top:100,left:150,direction:'down',speed:2.5},{top:200,left:350,direction:'up',speed:2.7},{top:300,left:200,direction:'right',speed:3},{top:250,left:100,direction:'left',speed:2.6}]},
        {gift:null, obstacles:[]}
    ];

    function loadLevel(level){
        obstacles.forEach(o=>o.element.remove());
        obstacles=[];
        gift.style.display='none';
        message.style.display='none';
        hitText.style.display='none';
        playerPos={top:gameHeight*0.875,left:gameWidth*0.04};
        player.style.top = playerPos.top+'px';
        player.style.left = playerPos.left+'px';

        const lvl = levels[level];
        if(lvl.gift){
            gift.style.display='block';
            gift.style.top = lvl.gift.top+'px';
            gift.style.left = lvl.gift.left+'px';
        }

        lvl.obstacles.forEach(obs=>{
            const div=document.createElement('div');
            div.classList.add('obstacle');
            div.style.top = obs.top+'px';
            div.style.left = obs.left+'px';
            div.dataset.direction = obs.direction;
            div.dataset.speed = obs.speed;
            div.innerHTML=`<div class="cake-base"><div class="icing"></div><div class="candle"></div></div>`;
            game.appendChild(div);
            obstacles.push({element:div,direction:obs.direction,speed:obs.speed});
        });

        // Safe Zone 2s
        safeZone = true;
        let flash = true;
        player.style.border = "2px solid #66ff66";
        const safeInterval = setInterval(()=>{
            player.style.border = flash ? "2px solid #66ff66" : "2px solid #ff3399";
            flash = !flash;
        }, 200);
        setTimeout(()=>{
            safeZone = false;
            player.style.border="none";
            clearInterval(safeInterval);
        },2000);

        scoreDisplay.textContent='Màn: '+(level+1);

        if(level === levels.length-1){
            message.style.display='block';
            setInterval(()=>{
                const h=document.createElement('div');
                h.className='heart';
                h.textContent='❤️';
                const size=Math.random()*30+20;
                h.style.fontSize=size+'px';
                const colors=['#ff3366','#ff66cc','#ff99aa','#ffccff','#ff0033'];
                h.style.color = colors[Math.floor(Math.random()*colors.length)];
                h.style.left=Math.random()*450+'px';
                h.style.top=Math.random()*350+'px';
                h.style.setProperty('--x',(Math.random()*100-50)+'px');
                game.appendChild(h);
                setTimeout(()=>h.remove(),2000);
            },200);
        }
    }

    function checkCollision(rect1,rect2){
        return rect1.left < rect2.left+rect2.width &&
            rect1.left+rect1.width > rect2.left &&
            rect1.top < rect2.top+rect2.height &&
            rect1.top+rect1.height > rect2.top;
    }

    function resetLevel(){
        loadLevel(currentLevel);
    }

    function gameLoop(){
        obstacles.forEach(obs=>{
            let t=parseFloat(obs.element.style.top);
            let l=parseFloat(obs.element.style.left);
            if(obs.direction==='down'){
                if(t >= gameHeight - obs.element.offsetHeight) obs.direction='up';
                else obs.element.style.top = t + obs.speed + 'px';
            }
            if(obs.direction==='up'){
                if(t <= 0) obs.direction='down';
                else obs.element.style.top = t - obs.speed + 'px';
            }
            if(obs.direction==='left'){
                if(l <= 0) obs.direction='right';
                else obs.element.style.left = l - obs.speed + 'px';
            }
            if(obs.direction==='right'){
                if(l >= gameWidth - obs.element.offsetWidth) obs.direction='left';
                else obs.element.style.left = l + obs.speed + 'px';
            }
        });

        if(!safeZone){
            const playerRect = player.getBoundingClientRect();
            for(const obs of obstacles){
                const obsRect = obs.element.getBoundingClientRect();
                if(checkCollision(playerRect, obsRect)){
                    safeZone = true;
                    hitText.style.display='block';
                    player.style.border = "3px solid red";
                    setTimeout(()=>{
                        hitText.style.display='none';
                        player.style.border="none";
                        resetLevel();
                    },1500);
                    break;
                }
            }
        }
        requestAnimationFrame(gameLoop);
    }

    // Menu
    const menu=document.getElementById("menu");
    const startBtn=document.getElementById("startBtn");
    const exitBtn=document.getElementById("exitBtn");
    let menuVisible=true;

    startBtn.addEventListener('click',()=>{
        menu.style.display='none';
        menuVisible=false;
        loadLevel(currentLevel);
        gameLoop();
    });
    exitBtn.addEventListener('click',()=>{
        document.getElementById("game-container").innerHTML=`<div style="width:100%;height:100%;display:flex;justify-content:center;align-items:center;font-size:6vw;color:#ff3399;font-weight:bold;background:#fff0f5;border-radius:15px;text-align:center;">Cảm ơn bé iu! 🎂💖</div>`;
    });

    // ------------------ Touch Controls ------------------
    const controls = {up: false, down:false, left:false, right:false};
    function movePlayer(){
        if(menuVisible) return;
        if(controls.up && playerPos.top>0) playerPos.top -= step;
        if(controls.down && playerPos.top<gameHeight-50) playerPos.top += step;
        if(controls.left && playerPos.left>0) playerPos.left -= step;
        if(controls.right && playerPos.left<gameWidth-50) playerPos.left += step;
        player.style.top = playerPos.top+'px';
        player.style.left = playerPos.left+'px';

        const playerRect = player.getBoundingClientRect();
        if(gift.style.display==='block'){
            const giftRect = gift.getBoundingClientRect();
            if(checkCollision(playerRect,giftRect)){
                currentLevel++;
                if(currentLevel<levels.length) loadLevel(currentLevel);
            }
        }
        requestAnimationFrame(movePlayer);
    }
    document.getElementById("up").addEventListener('touchstart',()=>controls.up=true);
    document.getElementById("up").addEventListener('touchend',()=>controls.up=false);
    document.getElementById("down").addEventListener('touchstart',()=>controls.down=true);
    document.getElementById("down").addEventListener('touchend',()=>controls.down=false);
    document.getElementById("left").addEventListener('touchstart',()=>controls.left=true);
    document.getElementById("left").addEventListener('touchend',()=>controls.left=false);
    document.getElementById("right").addEventListener('touchstart',()=>controls.right=true);
    document.getElementById("right").addEventListener('touchend',()=>controls.right=false);

    movePlayer();
</script>
</body>
</html>
