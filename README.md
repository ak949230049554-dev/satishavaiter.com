<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- SEO Meta Tags -->
    <meta name="description" content="satishaviator - Play the best crash game online. Real-time flying and betting experience.">
    <meta name="keywords" content="satishaviator, satish aviator, aviator game, Satish Coder, Crash Game">
    <meta name="author" content="Satish Coder">
    
    <!-- FAVICON -->
    <link rel="icon" type="image/png" href="https://cdn-icons-png.flaticon.com/512/7893/7893979.png">
    <link rel="apple-touch-icon" href="https://cdn-icons-png.flaticon.com/512/7893/7893979.png">

    <meta property="og:title" content="satishaviator - Aviator Game">
    <meta property="og:description" content="Click here to play satishaviator! Best real-time flying crash game.">
    <meta property="og:image" content="https://cdn-icons-png.flaticon.com/512/7893/7893979.png">
    <meta property="og:type" content="website">
    
    <title>satishaviator - Aviator</title>
    
    <style>
        /* --- CSS SECTION --- */
        :root { --red: #e50914; --bg: #000; --panel: #1b1c1d; --green: #28a745; --yellow: #ffc107; }
        
        body { background: #050505; color: #fff; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; display: flex; flex-direction: column; align-items: center; overflow: hidden; height: 100vh; }

        .app { width: 100%; max-width: 500px; height: 100%; display: flex; flex-direction: column; position: relative; background: #000; border-left: 1px solid #333; border-right: 1px solid #333; }

        /* Header */
        .header { display: flex; justify-content: space-between; align-items: center; padding: 12px 20px; background: var(--panel); border-bottom: 2px solid var(--red); z-index: 20; }
        .logo { display: flex; align-items: center; gap: 8px; color: var(--red); font-weight: 900; font-style: italic; font-size: 20px; text-shadow: 0 0 10px rgba(229,9,20,0.5); letter-spacing: 1px; cursor: pointer; transition: 0.2s; }
        .logo:active { transform: scale(0.95); }
        .logo img { width: 28px; filter: drop-shadow(0 0 5px var(--red)); }

        .bal-box { background: #000; padding: 6px 15px; border-radius: 20px; border: 1px solid var(--green); color: var(--green); font-weight: bold; font-size: 14px; box-shadow: 0 0 5px rgba(40,167,69,0.2); }

        /* Game Area */
        .game-area { height: 280px; background: radial-gradient(circle at center, #1a1a1a, #000); position: relative; overflow: hidden; display: flex; justify-content: center; align-items: center; margin: 10px; border-radius: 12px; border: 1px solid #222; flex-shrink: 0; }
        
        .bg-text { position: absolute; font-size: 32px; font-weight: 900; color: rgba(255, 255, 255, 0.03); z-index: 1; text-transform: uppercase; letter-spacing: 5px; pointer-events: none; text-align: center; }

        #multiplier { font-size: 70px; font-weight: 900; z-index: 10; text-shadow: 0 5px 15px #000; transition: color 0.1s; }
        #timer { font-size: 40px; color: var(--yellow); z-index: 10; font-weight: bold; }

        #curve { position: absolute; bottom: 0; left: 0; width: 0%; height: 0%; background: linear-gradient(to top right, rgba(229, 9, 20, 0.6), transparent); border-top: 4px solid var(--red); border-radius: 0 100% 0 0; z-index: 2; transition: 0.1s linear; }
        
        #plane { position: absolute; bottom: -50px; left: -50px; width: 80px; z-index: 5; display: none; filter: drop-shadow(0 0 15px rgba(229,9,20,0.8)); }
        .jet-active { animation: jetShake 0.05s infinite alternate; }
        @keyframes jetShake { from { transform: translate(0,0) rotate(-10deg); } to { transform: translate(2px, 2px) rotate(-10deg); } }

        /* Bet Section */
        .bet-section { display: flex; gap: 8px; padding: 0 10px; margin-bottom: 10px; flex-shrink: 0; }
        .bet-card { flex: 1; background: var(--panel); padding: 12px; border-radius: 10px; border: 1px solid #333; display: flex; flex-direction: column; gap: 8px; align-items: center; }
        .bet-card input { width: 90%; background: #000; border: 1px solid #444; color: #fff; padding: 8px; border-radius: 5px; text-align: center; font-size: 18px; font-weight: bold; outline: none; }
        .bet-card input:focus { border-color: var(--red); }

        .btn { width: 100%; height: 50px; border: none; border-radius: 8px; font-weight: 900; font-size: 16px; cursor: pointer; text-transform: uppercase; transition: 0.1s ease; }
        .btn-bet { background: var(--green); color: #fff; box-shadow: 0 4px 0 #1e7e34; }
        .btn-waiting { background: var(--yellow); color: #000; box-shadow: 0 4px 0 #cc9a06; }
        .btn-cashout { background: #ff9800; color: #fff; box-shadow: 0 4px 0 #e65100; }
        .btn-lost { background: #333; color: #777; cursor: not-allowed; }

        /* SCROLLABLE Fake Live Chat Section */
        .chat-section { flex-grow: 1; background: var(--panel); margin: 0 10px 10px 10px; border-radius: 12px; padding: 10px; border: 1px solid #222; overflow: hidden; display: flex; flex-direction: column; min-height: 0; } 
        .chat-header { font-size: 12px; color: #888; text-align: center; border-bottom: 1px solid #333; padding-bottom: 8px; margin-bottom: 10px; font-weight: bold; text-transform: uppercase; letter-spacing: 1px; flex-shrink: 0; }
        
        .chat-list { overflow-y: auto; flex-grow: 1; scrollbar-width: thin; scrollbar-color: #444 #111; padding-right: 5px; }
        .chat-list::-webkit-scrollbar { width: 4px; }
        .chat-list::-webkit-scrollbar-track { background: #111; }
        .chat-list::-webkit-scrollbar-thumb { background: #444; border-radius: 4px; }
        
        .chat-msg { display: flex; justify-content: space-between; align-items: center; background: #000; padding: 8px 12px; border-radius: 8px; margin-bottom: 8px; font-size: 13px; border: 1px solid #1a1a1a; animation: slideIn 0.3s ease-out; }
        @keyframes slideIn { from { opacity: 0; transform: translateY(-10px); } to { opacity: 1; transform: translateY(0); } }
        
        .user-box { display: flex; align-items: center; gap: 10px; }
        .user-box img { width: 36px; height: 36px; border-radius: 50%; border: 2px solid #444; object-fit: cover; box-shadow: 0 0 5px rgba(0,0,0,0.5); }
        .user-name { font-weight: bold; color: #ddd; }
        
        .win-info { display: flex; flex-direction: column; align-items: flex-end; }
        .win-mult { color: var(--green); font-weight: bold; font-size: 14px; }
        .win-amt { color: #aaa; font-size: 12px; font-weight: bold; }

        /* Highlight satishaviator */
        .highlight-satish { border: 1px solid var(--red); background: rgba(229, 9, 20, 0.1); }
        .highlight-satish .user-name { color: var(--red); font-weight: 900; }
        .highlight-satish img { border-color: var(--red); box-shadow: 0 0 10px rgba(229,9,20,0.8); }

        /* Tap to Play Overlay */
        #gate { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.98); z-index: 1000; display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
        .tap-plane { width: 120px; cursor: pointer; filter: drop-shadow(0 0 20px rgba(229,9,20,0.8)); animation: floatPlane 2s infinite ease-in-out; margin-bottom: 10px; }
        @keyframes floatPlane { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-15px); } }
        #gate h1 { color: var(--red); font-style: italic; margin-bottom: 30px; letter-spacing: 2px; cursor: pointer; }
        #gate button { padding: 18px 60px; background: var(--red); color: #fff; border: none; border-radius: 50px; font-size: 22px; font-weight: 900; cursor: pointer; box-shadow: 0 0 30px rgba(229,9,20,0.4); transition: 0.3s; }
        #gate button:hover, .tap-plane:hover { transform: scale(1.05); box-shadow: 0 0 50px rgba(229,9,20,0.6); }
    </style>
</head>
<body>

    <div id="gate">
        <img class="tap-plane" src="https://cdn-icons-png.flaticon.com/512/7893/7893979.png" onclick="startApp()" alt="Tap to Start Game">
        <h1 onclick="startApp()">satishaviator</h1>
        <button onclick="startApp()">START GAME</button>
    </div>

    <!-- AUDIO FILES -->
    <audio id="bgMusic" loop src="https://www.soundjay.com/ambient/sounds/office-ambience-01.mp3"></audio> 
    <audio id="flySnd" loop src="https://www.soundjay.com/mechanical/sounds/engine-hum-02.mp3"></audio>
    <audio id="crashSnd" src="https://www.soundjay.com/misc/sounds/fail-buzzer-01.mp3"></audio>

    <div class="app">
        <div class="header">
            <div class="logo" onclick="tapLogo()">
                <img src="https://cdn-icons-png.flaticon.com/512/7893/7893979.png" alt="icon">
                satishaviator
            </div>
            <div class="bal-box">₹ <span id="balance">40000.00</span></div>
        </div>

        <div class="game-area">
            <div class="bg-text">satishaviator</div>
            <div id="curve"></div>
            <img id="plane" src="https://cdn-icons-png.flaticon.com/512/7893/7893979.png" alt="Aviator Plane">
            <div id="multiplier" style="display:none;">1.00x</div>
            <div id="timer">WAITING... 3</div>
        </div>

        <div class="bet-section">
            <div class="bet-card">
                <!-- Value 10 se start hogi, max 8000 -->
                <input type="number" id="amt-1" value="10" min="10" max="8000" onblur="validate(this)">
                <button class="btn btn-bet" id="btn-1" onclick="handle(1)">BET</button>
            </div>
            <div class="bet-card">
                <input type="number" id="amt-2" value="10" min="10" max="8000" onblur="validate(this)">
                <button class="btn btn-bet" id="btn-2" onclick="handle(2)">BET</button>
            </div>
        </div>

        <div class="chat-section">
            <div class="chat-header">Live All Bets</div>
            <div class="chat-list" id="chat-content"></div>
        </div>
    </div>

    <script>
        let balance = 40000;
        let isFlying = false;
        let mult = 1.00;
        let crashAt = 0;
        let loop;
        let bets = { 1: { active: false, amt: 0 }, 2: { active: false, amt: 0 } };

        const bgMusic = document.getElementById('bgMusic');
        const flySnd = document.getElementById('flySnd');
        const crashSnd = document.getElementById('crashSnd');

        function startApp() {
            document.getElementById('gate').style.display = 'none';
            bgMusic.volume = 0.2; 
            bgMusic.play();
            
            setInterval(genChat, 1200);
            newRound();
        }

        function tapLogo() {
            alert("Welcome to satishaviator Official Game! Keep Playing & Winning!");
        }

        // Ye function bet ki limit ko check karega (10 se 8000 ke beech)
        function validate(el) {
            if (el.value > 8000) el.value = 8000;
            if (el.value < 10 || el.value === "") el.value = 10;
        }

        function handle(id) {
            let btn = document.getElementById('btn-'+id);
            let input = document.getElementById('amt-'+id);
            let val = parseFloat(input.value);

            // Double security: Bet place karte time bhi check karega
            if (isNaN(val) || val < 10) val = 10;
            if (val > 8000) val = 8000;
            input.value = val;

            if(!isFlying && !bets[id].active) {
                if(balance >= val) {
                    balance -= val;
                    document.getElementById('balance').innerText = balance.toFixed(2);
                    bets[id] = { active: true, amt: val };
                    btn.className = "btn btn-waiting";
                    btn.innerText = "WAITING...";
                    input.disabled = true;
                } else {
                    alert("Not enough balance!");
                }
            } else if(isFlying && bets[id].active) {
                let win = bets[id].amt * mult;
                balance += win;
                document.getElementById('balance').innerText = balance.toFixed(2);
                bets[id].active = false;
                btn.className = "btn btn-lost";
                btn.innerText = "WON ₹" + win.toFixed(2);
            }
        }

        function newRound() {
            isFlying = false; mult = 1.00;
            document.getElementById('multiplier').style.display = 'none';
            document.getElementById('multiplier').style.color = "#fff";
            document.getElementById('timer').style.display = 'block';
            document.getElementById('curve').style.width = '0%';
            document.getElementById('plane').style.display = 'none';

            [1, 2].forEach(id => {
                let btn = document.getElementById('btn-'+id);
                let input = document.getElementById('amt-'+id);
                if(bets[id].active) { 
                    btn.className = "btn btn-cashout"; 
                    btn.innerText = "CASH OUT"; 
                } else { 
                    btn.className = "btn btn-bet"; 
                    btn.innerText = "BET"; 
                    input.disabled = false;
                }
            });

            let sec = 3;
            let t = setInterval(() => {
                document.getElementById('timer').innerText = "WAITING... " + sec;
                sec--;
                if(sec < 0) { clearInterval(t); startFlight(); }
            }, 1000);
        }

        function startFlight() {
            isFlying = true;
            document.getElementById('timer').style.display = 'none';
            document.getElementById('multiplier').style.display = 'block';
            document.getElementById('plane').style.display = 'block';
            document.getElementById('plane').classList.add('jet-active');
            
            flySnd.volume = 0.5;
            flySnd.play();

            let r = Math.random();
            crashAt = r < 0.05 ? 1.00 : (r < 0.8 ? 1.1 + Math.random()*3 : 5 + Math.random()*120);
            if(crashAt === 1.00) { crash(); return; }

            loop = setInterval(() => {
                mult += (mult * 0.0035) + 0.001;
                if(mult >= crashAt) { crash(); }
                else {
                    document.getElementById('multiplier').innerText = mult.toFixed(2) + "x";
                    let p = Math.min((mult-1)/3.8, 1);
                    document.getElementById('curve').style.width = (p*100) + "%";
                    document.getElementById('curve').style.height = (p*100) + "%";
                    document.getElementById('plane').style.bottom = (p*220) + "px";
                    document.getElementById('plane').style.left = (p*350) + "px";

                    [1,2].forEach(id => {
                        if(bets[id].active) {
                            document.getElementById('btn-'+id).innerText = "CASH OUT ₹" + (bets[id].amt * mult).toFixed(2);
                        }
                    });
                }
            }, 50);
        }

        function crash() {
            clearInterval(loop); isFlying = false;
            
            flySnd.pause(); flySnd.currentTime = 0;
            crashSnd.volume = 1.0;
            crashSnd.play();

            document.getElementById('multiplier').innerText = "FLEW AWAY!";
            document.getElementById('multiplier').style.color = "#e50914";
            document.getElementById('plane').classList.remove('jet-active');

            [1,2].forEach(id => {
                if(bets[id].active) {
                    let btn = document.getElementById('btn-'+id);
                    btn.className = "btn btn-lost";
                    btn.innerText = "LOST";
                }
                bets[id].active = false;
            });
            setTimeout(newRound, 3000);
        }

        function genChat() {
            const list = document.getElementById('chat-content');
            
            const names = ["satishaviator", "Aman_99", "Rahul_Pro", "satishaviator", "Priya_Avi", "Vikash_ME"];
            let u = names[Math.floor(Math.random()*names.length)];
            
            let avatar = "";
            let extraClass = "";
            
            if(u === "satishaviator") {
                avatar = "https://cdn-icons-png.flaticon.com/512/3135/3135715.png";
                extraClass = "highlight-satish"; 
            } else {
                avatar = `https://i.pravatar.cc/100?u=${u}`;
            }

            let m = (1.1 + Math.random()*6).toFixed(2);
            // Chat me fake bets bhi lagbhag 10 se 8000 ke beech hi dikhayenge
            let b = [10, 50, 100, 500, 700, 2000, 8000][Math.floor(Math.random()*7)];

            let row = document.createElement('div');
            row.className = `chat-msg ${extraClass}`;
            
            row.innerHTML = `
                <div class="user-box">
                    <img src="${avatar}" alt="${u}">
                    <div class="user-name">${u}</div>
                </div>
                <div class="win-info">
                    <span class="win-mult">${m}x</span>
                    <span class="win-amt">Cashed Out ₹${(b*m).toFixed(0)}</span>
                </div>`;
            
            list.prepend(row);
            
            if(list.children.length > 60) list.removeChild(list.lastChild);
        }
    </script>
</body>
</html>
