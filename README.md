[Cantonese songs V8.txt](https://github.com/user-attachments/files/25937344/Cantonese.songs.V8.txt)
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="廣東歌迷">
    <title>廣東歌迷序會 - DJ Challenge</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Noto+Sans+HK:wght@400;700;900&display=swap" rel="stylesheet">

    <style>
        :root {
            --neon-cyan: #00f3ff;
            --neon-pink: #ff00ff;
            --neon-purple: #9d00ff;
            --neon-yellow: #fbbf24;
            --dark-bg: #0b0c10;
        }

        body {
            background-color: var(--dark-bg);
            background-image: 
                radial-gradient(circle at 15% 50%, rgba(0, 243, 255, 0.1), transparent 25%),
                radial-gradient(circle at 85% 30%, rgba(255, 0, 255, 0.1), transparent 25%);
            font-family: 'Noto Sans HK', sans-serif;
            touch-action: manipulation;
            -webkit-user-select: none;
            overflow-x: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
            color: white;
            padding: 1rem;
        }

        .font-arcade { font-family: 'Orbitron', sans-serif; }

        .neon-text-cyan { color: var(--neon-cyan); text-shadow: 0 0 5px var(--neon-cyan), 0 0 15px var(--neon-cyan); }
        .neon-text-pink { color: var(--neon-pink); text-shadow: 0 0 5px var(--neon-pink), 0 0 15px var(--neon-pink); }
        .neon-text-yellow { color: var(--neon-yellow); text-shadow: 0 0 5px var(--neon-yellow), 0 0 15px var(--neon-yellow); }
        
        .arcade-panel {
            background: rgba(15, 23, 42, 0.85);
            backdrop-filter: blur(15px);
            border-top: 2px solid rgba(255,255,255,0.1);
            border-bottom: 2px solid rgba(0,0,0,0.8);
            border: 2px solid var(--neon-cyan);
            box-shadow: 0 0 10px var(--neon-cyan), inset 0 0 10px rgba(0, 243, 255, 0.3);
            border-radius: 1.5rem;
            padding: 1.5rem;
            width: 100%;
            max-width: 32rem; 
            position: relative;
            display: none; 
        }
        
        #home-screen { display: flex; flex-direction: column; } 

        .vinyl-record {
            background: repeating-radial-gradient(#111, #111 4px, #222 5px, #222 6px);
            box-shadow: 0 0 20px rgba(0,0,0,0.8), 0 0 15px var(--neon-purple);
            width: 9rem;
            height: 9rem;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto;
            transition: transform 0.5s linear;
        }
        
        .animate-spin-slow { animation: spin 4s linear infinite; }
        @keyframes spin { 100% { transform: rotate(360deg); } }

        .game-btn { 
            transition: all 0.2s; 
            width: 100%;
            padding: 1rem;
            border-radius: 0.75rem;
            font-size: 1.125rem;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.75rem;
            margin-bottom: 0.75rem;
            cursor: pointer;
        }
        .game-btn:active { transform: scale(0.95); }
        .game-btn:disabled { opacity: 0.7; transform: none; cursor: not-allowed; }

        .btn-cyan { background-color: #1f2937; border: 1px solid var(--neon-cyan); color: #22d3ee; box-shadow: 0 0 10px rgba(0,243,255,0.2); }
        .btn-purple { background-color: #1f2937; border: 1px solid #a855f7; color: #c084fc; box-shadow: 0 0 10px rgba(168,85,247,0.2); }
        .btn-pink { background-color: #1f2937; border: 1px solid var(--neon-pink); color: #f472b6; box-shadow: 0 0 15px rgba(255,0,255,0.4); }
        
        /* 6 個選項的按鈕樣式，縮小字體確保不會破版 */
        .btn-option {
            background-color: #1f2937;
            border: 1px solid #4b5563;
            color: white;
            padding: 0.5rem;
            border-radius: 0.5rem;
            font-size: 0.85rem;
            font-weight: bold;
            transition: all 0.2s;
            cursor: pointer;
            width: 100%;
            word-break: break-word;
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 3.5rem;
            line-height: 1.2;
        }
        @media (min-width: 640px) {
            .btn-option { font-size: 1rem; padding: 0.75rem; }
        }
        .btn-option:hover { border-color: var(--neon-cyan); box-shadow: 0 0 10px rgba(0,243,255,0.5); }
        .btn-option:disabled { cursor: not-allowed; }

        .fade-in { animation: fadeIn 0.4s ease-in; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        
        /* 等化器 */
        .eq-bar { width: 6px; background-color: var(--neon-cyan); border-radius: 4px; transition: height 0.1s ease; box-shadow: 0 0 8px var(--neon-cyan); }
        .eq-playing .eq-bar:nth-child(1) { animation: eq-bounce 0.8s infinite alternate ease-in-out; }
        .eq-playing .eq-bar:nth-child(2) { animation: eq-bounce 0.5s infinite alternate ease-in-out 0.2s; background-color: var(--neon-pink); box-shadow: 0 0 8px var(--neon-pink);}
        .eq-playing .eq-bar:nth-child(3) { animation: eq-bounce 0.9s infinite alternate ease-in-out 0.4s; }
        .eq-playing .eq-bar:nth-child(4) { animation: eq-bounce 0.6s infinite alternate ease-in-out 0.1s; background-color: var(--neon-pink); box-shadow: 0 0 8px var(--neon-pink);}
        .eq-playing .eq-bar:nth-child(5) { animation: eq-bounce 0.7s infinite alternate ease-in-out 0.3s; }

        @keyframes eq-bounce { 0% { height: 8px; } 100% { height: 35px; } }
        
        audio::-webkit-media-controls { display: none !important; }
    </style>
</head>
<body>

    <audio id="audio-player" preload="auto"></audio>

    <!-- 主畫面 -->
    <div id="home-screen" class="arcade-panel fade-in">
        <div class="text-6xl mb-4 text-center w-full flex justify-center">
            <i class="fas fa-compact-disc text-gray-400"></i>
        </div>
        <h1 class="text-3xl font-black mb-2 text-center tracking-wider neon-text-cyan font-arcade">
            CANTOPOP DJ
        </h1>
        <h2 class="text-xl font-bold text-center text-white mb-1">廣東歌迷序會</h2>
        <p class="text-gray-400 text-center text-xs font-arcade mb-8">Hardcore 6-Options Edition</p>

        <div class="space-y-2 w-full">
            <button onclick="startGame('year')" class="game-btn btn-cyan">
                <i class="fas fa-calendar-alt"></i> MODE 1: 估年份
            </button>
            <button onclick="startGame('singer')" class="game-btn btn-purple">
                <i class="fas fa-user-astronaut"></i> MODE 2: 估歌手
            </button>
            <button onclick="startGame('song')" class="game-btn btn-pink">
                <i class="fas fa-music"></i> MODE 3: 估歌名
            </button>
        </div>
    </div>

    <!-- 遊戲畫面 -->
    <div id="game-screen" class="arcade-panel hidden fade-in" style="border-color: var(--neon-purple);">
        
        <div class="flex justify-between items-center bg-black/50 p-3 rounded-lg border border-gray-700 mb-4">
            <button onclick="returnToHome()" class="text-gray-400 hover:text-white">
                <i class="fas fa-power-off text-xl"></i>
            </button>
            <span id="game-title" class="text-sm font-bold font-arcade text-purple-400 tracking-widest">GUESS THE SONG</span>
            <div class="text-pink-500 font-arcade text-lg">
                <span id="current-question">1</span>/<span id="total-questions">10</span>
            </div>
        </div>

        <div class="flex flex-col items-center justify-center mb-4 relative w-full">
            <div id="equalizer" class="flex gap-2 items-end h-[35px] mb-3">
                <div class="eq-bar h-[8px]"></div><div class="eq-bar h-[8px]"></div><div class="eq-bar h-[8px]"></div><div class="eq-bar h-[8px]"></div><div class="eq-bar h-[8px]"></div>
            </div>

            <div id="disc-cover" class="vinyl-record">
                <div class="w-12 h-12 bg-gradient-to-br from-cyan-400 to-purple-600 rounded-full border-2 border-black flex items-center justify-center">
                    <div class="w-2 h-2 bg-black rounded-full"></div>
                </div>
            </div>
            
            <div class="mt-4 bg-gray-900 p-2 rounded-xl border border-gray-700 flex flex-col items-center w-full max-w-[200px]">
                <p id="audio-status" class="text-[10px] text-cyan-300 font-arcade mb-1 h-3 uppercase tracking-widest">SYSTEM READY</p>
                <button id="play-btn" onclick="togglePlay()" class="w-full py-2 bg-gradient-to-r from-cyan-500 to-blue-600 rounded-lg text-white font-bold text-sm shadow-[0_0_10px_rgba(0,243,255,0.4)] active:scale-95 transition-all flex items-center justify-center gap-2" disabled>
                    <i class="fas fa-spinner fa-spin"></i> 載入中...
                </button>
            </div>
        </div>

        <!-- 顯示當前已知的資訊 -->
        <div id="question-info" class="mb-4 text-center font-bold text-base h-6 w-full flex items-center justify-center"></div>

        <!-- 答題區域 (2列，3行 = 6個選項) -->
        <div id="answer-area" class="grid grid-cols-2 gap-2 w-full">
            <!-- 按鈕由 JS 生成 -->
        </div>
    </div>

    <!-- 結算畫面 -->
    <div id="result-screen" class="arcade-panel hidden fade-in" style="border-color: var(--neon-yellow);">
        <h2 class="text-4xl text-center font-arcade text-yellow-400 mb-2 neon-text-cyan" style="text-shadow: 0 0 10px #fbbf24;">GAME OVER</h2>
        <p class="text-gray-300 text-center mb-6 font-arcade text-sm">STAGE CLEARED</p>
        
        <div class="bg-black/50 p-6 rounded-xl border border-gray-700 mb-6 text-center">
            <p class="text-gray-400 text-sm mb-2">FINAL SCORE</p>
            <p class="text-6xl font-black font-arcade text-white"><span id="final-score" class="text-cyan-400">0</span><span class="text-2xl text-gray-600">/</span><span id="max-score" class="text-2xl text-gray-500">10</span></p>
        </div>

        <div class="mb-8 p-4 text-center rounded-lg bg-yellow-900/30 border border-yellow-500/50 shadow-[0_0_10px_rgba(251,191,36,0.2)] w-full">
            <p class="text-xs text-gray-400 font-arcade mb-1">YOUR RANK</p>
            <p id="rank-display" class="text-2xl font-bold text-yellow-400 tracking-wider"></p>
            <p id="rank-desc" class="text-sm text-gray-300 mt-2"></p>
        </div>
        
        <button onclick="returnToHome()" class="game-btn" style="background-color: #1f2937; border: 1px solid var(--neon-yellow); color: var(--neon-yellow); box-shadow: 0 0 15px rgba(251,191,36,0.3); font-family: 'Orbitron', sans-serif; letter-spacing: 0.1em;">
            RESTART SYSTEM
        </button>
    </div>

    <script type="text/javascript">
        // 為了確保在 GitHub Pages 正常運行，加入全域錯誤捕捉
        window.onerror = function(msg, url, line) {
            console.error("Error: " + msg + " at line " + line);
        };

        // 核心歌庫 (已移除 Dear Jane 到底發生過什麼事)
        let songDatabase = [
            // 陳奕迅
            { title: '富士山下', artist: '陳奕迅', year: 2006, gender: 'M', query: '陳奕迅 富士山下' },
            { title: '陀飛輪', artist: '陳奕迅', year: 2010, gender: 'M', query: '陳奕迅 陀飛輪' },
            { title: '單車', artist: '陳奕迅', year: 2001, gender: 'M', query: '陳奕迅 單車' },
            { title: '明年今日', artist: '陳奕迅', year: 2002, gender: 'M', query: '陳奕迅 明年今日' },
            { title: 'K歌之王', artist: '陳奕迅', year: 2000, gender: 'M', query: '陳奕迅 K歌之王' },
            { title: '人車誌', artist: '陳奕迅', year: 2006, gender: 'M', query: '陳奕迅 人車誌' },
            { title: '重口味', artist: '陳奕迅', year: 2012, gender: 'M', query: '陳奕迅 重口味' },
            { title: '苦瓜', artist: '陳奕迅', year: 2011, gender: 'M', query: '陳奕迅 苦瓜' },
            { title: '無條件', artist: '陳奕迅', year: 2015, gender: 'M', query: '陳奕迅 無條件' },
            
            // 陳健安
            { title: '創作者的派對', artist: '陳健安', year: 2023, gender: 'M', query: '陳健安 創作者的派對' },
            { title: '好好掛住', artist: '陳健安', year: 2023, gender: 'M', query: '陳健安 好好掛住' },
            { title: '在錯誤的宇宙尋找愛', artist: '陳健安', year: 2019, gender: 'M', query: '陳健安 在錯誤的宇宙尋找愛' },
            { title: '仍然是那個少年', artist: '陳健安', year: 2023, gender: 'M', query: '陳健安 仍然是那個少年' },
            
            // Jay Fung 馮允謙
            { title: '報復式浪漫', artist: 'Jay Fung', year: 2022, gender: 'M', query: '馮允謙 報復式浪漫' },
            { title: '地球來的人', artist: 'Jay Fung', year: 2020, gender: 'M', query: '馮允謙 地球來的人' },
            { title: '思念即地獄', artist: 'Jay Fung', year: 2021, gender: 'M', query: '馮允謙 思念即地獄' },
            { title: '給缺席的人唱首歌', artist: 'Jay Fung', year: 2022, gender: 'M', query: '馮允謙 給缺席的人唱首歌' },
            { title: '收到收到', artist: 'Jay Fung', year: 2023, gender: 'M', query: '馮允謙 收到收到' },
            
            // 湯令山 Gareth.T
            { title: 'Boyfriend Material', artist: '湯令山', year: 2021, gender: 'M', query: 'Gareth.T Boyfriend Material' },
            { title: '勁浪漫 超溫馨', artist: '湯令山', year: 2021, gender: 'M', query: 'Gareth.T 勁浪漫超溫馨' },
            { title: '笑住喊', artist: '湯令山', year: 2022, gender: 'M', query: 'Gareth.T 笑住喊' },
            { title: '國際孤獨等級', artist: '湯令山', year: 2023, gender: 'M', query: 'Gareth.T 國際孤獨等級' },

            // 其他熱門男歌手
            { title: '記憶棉', artist: 'MC 張天賦', year: 2021, gender: 'M', query: 'MC 張天賦 記憶棉' },
            { title: '老派約會之必要', artist: 'MC 張天賦', year: 2022, gender: 'M', query: 'MC 張天賦 老派約會之必要' },
            { title: '一人之境', artist: '林家謙', year: 2020, gender: 'M', query: '林家謙 一人之境' },
            { title: '時光倒流一句話', artist: '林家謙', year: 2020, gender: 'M', query: '林家謙 時光倒流一句話' },
            { title: '隱形遊樂場', artist: '張敬軒', year: 2023, gender: 'M', query: '張敬軒 隱形遊樂場' },
            { title: '櫻花樹下', artist: '張敬軒', year: 2008, gender: 'M', query: '張敬軒 櫻花樹下' },
            
            // 女歌手
            { title: '至少做一件離譜的事', artist: 'Kiri T', year: 2024, gender: 'F', query: 'Kiri T 至少做一件離譜的事' },
            { title: '歧義種子', artist: 'Kiri T', year: 2023, gender: 'F', query: 'Kiri T 歧義種子' },
            { title: '趁你旅行時搬走', artist: 'Moon Tang', year: 2024, gender: 'F', query: 'Moon Tang 趁你旅行時搬走' },
            { title: '遲了悔改', artist: 'Moon Tang', year: 2022, gender: 'F', query: 'Moon Tang 遲了悔改' }, 
            
            { title: '我的驕傲', artist: '容祖兒', year: 2003, gender: 'F', query: '容祖兒 我的驕傲' },
            { title: '心淡', artist: '容祖兒', year: 2003, gender: 'F', query: '容祖兒 心淡' },
            { title: '囍帖街', artist: '謝安琪', year: 2008, gender: 'F', query: '謝安琪 囍帖街' },
            { title: '鍾無艷', artist: '謝安琪', year: 2007, gender: 'F', query: '謝安琪 鍾無艷' },
            { title: '凡星', artist: '陳蕾', year: 2021, gender: 'F', query: '陳蕾 凡星' },
            { title: '少女的祈禱', artist: '楊千嬅', year: 2000, gender: 'F', query: '楊千嬅 少女的祈禱' },
            { title: '大哥', artist: '衛蘭', year: 2005, gender: 'F', query: '衛蘭 大哥' },
            { title: '假使世界原來不像你預期', artist: '方皓玟', year: 2018, gender: 'F', query: '方皓玟 假使世界原來不像你預期' },

            // 組合 
            { title: '天梯', artist: 'C AllStar', year: 2010, gender: 'G', query: 'C AllStar 天梯' },
            { title: '留下來的人', artist: 'C AllStar', year: 2021, gender: 'G', query: 'C AllStar 留下來的人' },
            { title: '專業失戀30年', artist: 'C AllStar', year: 2016, gender: 'G', query: 'C AllStar 專業失戀30年' },
            { title: '沒明日的恐懼', artist: 'C AllStar', year: 2021, gender: 'G', query: 'C AllStar 沒明日的恐懼' },
            { title: '銀河修理員', artist: 'Dear Jane', year: 2020, gender: 'G', query: 'Dear Jane 銀河修理員' },
            
            // 單飛成員 
            { title: '人類群星閃耀時', artist: '柳應廷 Jer', year: 2021, gender: 'M', query: '柳應廷 人類群星閃耀時' },
            { title: '狂人日記', artist: '柳應廷 Jer', year: 2021, gender: 'M', query: '柳應廷 狂人日記' },
            { title: 'E先生 連環不幸事件', artist: '呂爵安 Edan', year: 2021, gender: 'M', query: '呂爵安 E先生' },
            { title: '留一天與你喘息', artist: '陳卓賢 Ian', year: 2022, gender: 'M', query: '陳卓賢 留一天與你喘息' },
            { title: 'Megahit', artist: '盧瀚霆 Anson Lo', year: 2021, gender: 'M', query: '盧瀚霆 Megahit' }
        ];

        let currentMode = '';
        let gameQueue = [];
        let currentIndex = 0;
        let score = 0;
        let currentAudioUrl = '';
        let audioPlayer;
        const TOTAL_QUESTIONS = 10;
        let hasInteracted = false;

        // 安全播放函式，避免 Safari 阻擋導致程式崩潰
        function safePlay(player) {
            try {
                let playPromise = player.play();
                if (playPromise !== undefined) {
                    playPromise.catch(e => {
                        console.log("Autoplay blocked: ", e);
                        document.getElementById('audio-status').innerText = "⚠️ 請點擊播放";
                    });
                }
            } catch (err) {
                console.log("Play sync error", err);
            }
        }

        // 超時 Fetch 函式，兼容舊版瀏覽器
        function fetchWithTimeout(url, timeout = 4000) {
            return new Promise((resolve, reject) => {
                const timer = setTimeout(() => reject(new Error('Timeout')), timeout);
                fetch(url)
                    .then(response => {
                        clearTimeout(timer);
                        resolve(response);
                    })
                    .catch(err => {
                        clearTimeout(timer);
                        reject(err);
                    });
            });
        }

        document.addEventListener('DOMContentLoaded', () => {
            audioPlayer = document.getElementById('audio-player');

            audioPlayer.addEventListener('play', () => {
                document.getElementById('disc-cover').classList.add('animate-spin-slow');
                document.getElementById('equalizer').classList.add('eq-playing');
                document.getElementById('audio-status').innerText = "▶ NOW PLAYING";
                document.getElementById('play-btn').innerHTML = '<i class="fas fa-pause"></i> PAUSE';
                document.getElementById('play-btn').className = "w-full py-2 bg-gradient-to-r from-pink-500 to-red-600 rounded-lg text-white font-bold text-sm shadow-[0_0_10px_rgba(255,0,255,0.4)] active:scale-95 transition-all flex items-center justify-center gap-2";
            });

            audioPlayer.addEventListener('pause', () => {
                document.getElementById('disc-cover').classList.remove('animate-spin-slow');
                document.getElementById('equalizer').classList.remove('eq-playing');
                document.getElementById('audio-status').innerText = "⏸ PAUSED";
                document.getElementById('play-btn').innerHTML = '<i class="fas fa-play"></i> PLAY AUDIO';
                document.getElementById('play-btn').className = "w-full py-2 bg-gradient-to-r from-cyan-500 to-blue-600 rounded-lg text-white font-bold text-sm shadow-[0_0_10px_rgba(0,243,255,0.4)] active:scale-95 transition-all flex items-center justify-center gap-2";
            });

            audioPlayer.addEventListener('ended', () => {
                document.getElementById('disc-cover').classList.remove('animate-spin-slow');
                document.getElementById('equalizer').classList.remove('eq-playing');
                document.getElementById('audio-status').innerText = "⏹ TRACK ENDED";
                document.getElementById('play-btn').innerHTML = '<i class="fas fa-redo"></i> REPLAY';
            });
        });

        // 綁定到 window 確保全域可用
        window.togglePlay = function() {
            if (!currentAudioUrl) return;
            if (audioPlayer.paused) {
                safePlay(audioPlayer);
            } else {
                audioPlayer.pause();
            }
        };

        function stopMusic() {
            if (audioPlayer && !audioPlayer.paused) {
                audioPlayer.pause();
            }
            if (audioPlayer) audioPlayer.currentTime = 0;
            document.getElementById('disc-cover').classList.remove('animate-spin-slow');
            document.getElementById('equalizer').classList.remove('eq-playing');
        }

        function showScreen(screenId) {
            const screens = ['home-screen', 'game-screen', 'result-screen'];
            screens.forEach(id => {
                const el = document.getElementById(id);
                if (id === screenId) {
                    el.classList.remove('hidden');
                    el.classList.add('flex', 'flex-col');
                } else {
                    el.classList.add('hidden');
                    el.classList.remove('flex', 'flex-col');
                }
            });
        }

        function shuffle(array) {
            let currentIndex = array.length, randomIndex;
            while (currentIndex != 0) {
                randomIndex = Math.floor(Math.random() * currentIndex);
                currentIndex--;
                [array[currentIndex], array[randomIndex]] = [array[randomIndex], array[currentIndex]];
            }
            return array;
        }

        function getSimilarYear(targetYear) {
            const offsets = [-4, -3, -2, -1, 1, 2, 3, 4, 5];
            return targetYear + offsets[Math.floor(Math.random() * offsets.length)];
        }

        window.startGame = function(mode) {
            // 解鎖 iOS 音訊限制
            if (audioPlayer) {
                audioPlayer.src = "data:audio/wav;base64,UklGRigAAABXQVZFZm10IBIAAAABAAEARKwAAIhYAQACABAAAABkYXRhAgAAAAEA";
                safePlay(audioPlayer);
            }
            
            currentMode = mode;
            score = 0;
            currentIndex = 0;
            
            let shuffledSongs = shuffle([...songDatabase]);
            gameQueue = shuffledSongs.slice(0, TOTAL_QUESTIONS);

            showScreen('game-screen');
            
            const titles = {
                'year': 'MODE 1: 估年份',
                'singer': 'MODE 2: 估歌手',
                'song': 'MODE 3: 估歌名'
            };
            document.getElementById('game-title').innerText = titles[mode];

            prepareAndLoadQuestion();
        };

        // 準備題目 (包含自動刪除與替換機制)
        async function prepareAndLoadQuestion() {
            stopMusic();
            const answerArea = document.getElementById('answer-area');
            const playBtn = document.getElementById('play-btn');
            const status = document.getElementById('audio-status');
            const infoDisplay = document.getElementById('question-info');

            // 顯示載入中
            document.getElementById('current-question').innerText = currentIndex + 1;
            document.getElementById('total-questions').innerText = TOTAL_QUESTIONS;
            infoDisplay.innerText = "";
            answerArea.innerHTML = '<div class="col-span-2 text-center text-cyan-400 font-bold py-4">🎵 正在尋找音源...</div>';
            playBtn.disabled = true;
            playBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> LOADING...';
            status.innerText = "CONNECTING...";

            let currentSong = gameQueue[currentIndex];
            let audioFound = false;
            
            // 嘗試抓取音樂，若失敗則刪除該歌並替換，最多試 5 次防止無窮迴圈
            for (let attempts = 0; attempts < 5; attempts++) {
                try {
                    let url = `https://itunes.apple.com/search?term=${encodeURIComponent(currentSong.query)}&entity=song&country=hk&limit=1`;
                    let response = await fetchWithTimeout(url, 3000);
                    let data = await response.json();
                    
                    if (data.results && data.results.length > 0) {
                        currentAudioUrl = data.results[0].previewUrl;
                        audioPlayer.src = currentAudioUrl;
                        audioFound = true;
                        break; // 成功找到音樂，跳出迴圈
                    } else {
                        throw new Error("No preview available");
                    }
                } catch (err) {
                    console.log("找不到音樂，刪除並替換:", currentSong.title);
                    // 從總庫刪除
                    songDatabase = songDatabase.filter(s => s.title !== currentSong.title);
                    
                    // 隨機選一首新的且不在 Queue 中的歌
                    let newSong;
                    let findAttempts = 0;
                    do {
                        newSong = songDatabase[Math.floor(Math.random() * songDatabase.length)];
                        findAttempts++;
                    } while (gameQueue.includes(newSong) && findAttempts < 20);
                    
                    currentSong = newSong;
                    gameQueue[currentIndex] = currentSong;
                }
            }

            // 渲染畫面
            playBtn.disabled = false;
            status.innerText = "READY";
            playBtn.innerHTML = '<i class="fas fa-play"></i> 播放音樂';
            
            if (audioFound) {
                safePlay(audioPlayer);
            } else {
                // 如果連續 5 首失敗 (極端情況)，給一個假按鈕
                status.innerText = "⚠️ 音樂載入失敗";
                playBtn.innerHTML = '<i class="fas fa-exclamation-triangle"></i> 盲估模式';
            }

            renderOptions(currentSong);
        }

        // 渲染文字與按鈕
        function renderOptions(currentSong) {
            const answerArea = document.getElementById('answer-area');
            const infoDisplay = document.getElementById('question-info');
            answerArea.innerHTML = ''; 

            // 根據模式設定提示文字
            if (currentMode === 'year') {
                infoDisplay.innerText = `《${currentSong.title}》 - ${currentSong.artist}`;
                infoDisplay.className = "mb-4 text-center font-bold text-base text-gray-200 w-full break-words";
            } else if (currentMode === 'singer') {
                // 估歌手：不顯示歌名
                infoDisplay.innerText = `❓ 請聆聽音樂猜測歌手 ❓`;
                infoDisplay.className = "mb-4 text-center font-bold text-base text-pink-400 w-full break-words";
            } else if (currentMode === 'song') {
                // 估歌名：不顯示歌手
                infoDisplay.innerText = `❓ 請聆聽音樂猜測歌名 ❓`;
                infoDisplay.className = "mb-4 text-center font-bold text-base text-cyan-300 w-full break-words";
            }

            let options = [];
            let correctAns;
            
            // 產生 6 個選項
            if (currentMode === 'year') {
                correctAns = currentSong.year;
                options.push(correctAns);
                while (options.length < 6) {
                    let fakeYear = getSimilarYear(correctAns);
                    if (fakeYear >= 1990 && fakeYear <= 2026 && !options.includes(fakeYear)) {
                        options.push(fakeYear);
                    }
                }
            } else if (currentMode === 'singer') {
                correctAns = currentSong.artist;
                options.push(correctAns);
                let pool = songDatabase.filter(s => s.gender === currentSong.gender && s.artist !== correctAns);
                let uniqueArtists = [...new Set(pool.map(s => s.artist))];
                uniqueArtists = shuffle(uniqueArtists);
                for (let i = 0; i < uniqueArtists.length; i++) {
                    if (options.length >= 6) break;
                    options.push(uniqueArtists[i]);
                }
                
                if(options.length < 6) {
                    let allUniqueArtists = [...new Set(songDatabase.map(s => s.artist))];
                    allUniqueArtists = shuffle(allUniqueArtists);
                    for (let i = 0; i < allUniqueArtists.length; i++) {
                        if (options.length >= 6) break;
                        if (!options.includes(allUniqueArtists[i])) {
                            options.push(allUniqueArtists[i]);
                        }
                    }
                }
            } else if (currentMode === 'song') {
                correctAns = currentSong.title;
                options.push(correctAns);
                let pool = songDatabase.filter(s => s.artist === currentSong.artist && s.title !== correctAns);
                
                if (pool.length < 5) {
                    let extraPool = songDatabase.filter(s => s.gender === currentSong.gender && s.title !== correctAns && !pool.includes(s));
                    pool = pool.concat(extraPool);
                }
                pool = shuffle(pool);
                for (let i = 0; i < pool.length; i++) {
                    if (options.length >= 6) break;
                    if (!options.includes(pool[i].title)) {
                        options.push(pool[i].title);
                    }
                }
                
                if (options.length < 6) {
                    let allPool = shuffle([...songDatabase]);
                     for (let i = 0; i < allPool.length; i++) {
                        if (options.length >= 6) break;
                        if (!options.includes(allPool[i].title)) {
                            options.push(allPool[i].title);
                        }
                    }
                }
            }

            options = shuffle(options);
            
            options.forEach(opt => {
                const btn = document.createElement('button');
                btn.className = "btn-option";
                btn.innerText = opt + (currentMode === 'year' ? ' 年' : '');
                btn.onclick = () => window.checkButtonAnswer(opt, correctAns, btn);
                answerArea.appendChild(btn);
            });
        }

        window.checkButtonAnswer = function(selected, correct, btnElement) {
            const buttons = document.getElementById('answer-area').querySelectorAll('button');
            buttons.forEach(b => b.disabled = true);

            if (selected === correct) {
                btnElement.style.backgroundColor = '#064e3b'; 
                btnElement.style.borderColor = '#34d399'; 
                btnElement.style.color = '#34d399';
                score++;
            } else {
                btnElement.style.backgroundColor = '#7f1d1d'; 
                btnElement.style.borderColor = '#f87171'; 
                btnElement.style.color = '#f87171';
                
                buttons.forEach(b => {
                    if (b.innerText.replace(' 年', '') == correct) {
                        b.style.borderColor = '#34d399';
                        b.style.color = '#34d399';
                    }
                });
            }
            setTimeout(nextQuestion, 1500);
        };

        function nextQuestion() {
            currentIndex++;
            if (currentIndex < gameQueue.length) {
                prepareAndLoadQuestion(); 
            } else {
                endGame();
            }
        }

        function endGame() {
            stopMusic();
            showScreen('result-screen');
            
            document.getElementById('final-score').innerText = score;
            
            const rankDisplay = document.getElementById('rank-display');
            const rankDesc = document.getElementById('rank-desc');
            
            if (score === 10) {
                rankDisplay.innerText = "👑 金曲歌神";
                rankDisplay.style.color = "var(--neon-yellow)";
                rankDisplay.style.textShadow = "0 0 10px var(--neon-yellow)";
                rankDesc.innerText = "太癲啦！你係咪喺 K房住㗎？";
            } else if (score >= 7) {
                rankDisplay.innerText = "🌟 廣東歌達人";
                rankDisplay.style.color = "var(--neon-cyan)";
                rankDisplay.style.textShadow = "0 0 5px var(--neon-cyan)";
                rankDesc.innerText = "好勁！平時一定聽好多廣東歌！";
            } else if (score >= 4) {
                rankDisplay.innerText = "🎧 普通樂迷";
                rankDisplay.style.color = "#c084fc"; 
                rankDisplay.style.textShadow = "none";
                rankDesc.innerText = "唔錯啦，流行曲你都略懂一二！";
            } else {
                rankDisplay.innerText = "🌱 新手樂迷";
                rankDisplay.style.color = "#9ca3af"; 
                rankDisplay.style.textShadow = "none";
                rankDesc.innerText = "聽多啲本地歌啦，香港樂壇需要你！";
            }
        }

        window.returnToHome = function() {
            stopMusic();
            showScreen('home-screen');
        };
    </script>
</body>
</html>
