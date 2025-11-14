<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Torihiplay - 獨立遊戲開發者</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            line-height: 1.8;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            background-attachment: fixed;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.98);
            border-radius: 20px;
            padding: 50px 40px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 15px;
            color: #2d3748;
        }

        .header .subtitle {
            font-size: 1.3em;
            color: #4a5568;
            margin-top: 10px;
        }

        hr {
            border: none;
            border-top: 2px solid #e2e8f0;
            margin: 40px 0;
        }

        h2 {
            color: #2d3748;
            font-size: 2em;
            margin-bottom: 25px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .about-section {
            background: #f7fafc;
            padding: 25px;
            border-radius: 12px;
            margin-bottom: 30px;
            border-left: 4px solid #667eea;
        }

        .about-section pre {
            background: #2d3748;
            color: #e2e8f0;
            padding: 20px;
            border-radius: 8px;
            overflow-x: auto;
            font-family: 'Monaco', 'Courier New', monospace;
            font-size: 0.95em;
        }

        .game-card {
            padding: 30px;
            border-radius: 16px;
            margin-bottom: 30px;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }

        .game-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
        }

        .game-card.dino {
            background: linear-gradient(135deg, #ffeaa7 0%, #fdcb6e 100%);
            border-color: #fdcb6e;
        }

        .game-card.rolling {
            background: linear-gradient(135deg, #a29bfe 0%, #6c5ce7 100%);
            color: white;
            border-color: #6c5ce7;
        }

        .game-card.rolling a {
            color: white;
            text-decoration: underline;
        }

        .game-card.hopi {
            background: linear-gradient(135deg, #55efc4 0%, #00b894 100%);
            border-color: #00b894;
        }

        .game-card h3 {
            font-size: 1.9em;
            margin-bottom: 12px;
            font-weight: 700;
        }

        .game-card h4 {
            font-size: 1.4em;
            margin-bottom: 15px;
            font-weight: 600;
            opacity: 0.95;
        }

        .game-card p {
            margin-bottom: 15px;
            font-size: 1.1em;
            line-height: 1.7;
        }

        .game-card ul {
            margin: 15px 0;
            padding-left: 20px;
        }

        .game-card li {
            margin: 10px 0;
            font-size: 1.05em;
        }

        .game-card a {
            color: #2d3748;
            font-weight: 600;
            text-decoration: none;
            display: inline-block;
            margin-top: 10px;
            padding: 10px 20px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 8px;
            transition: all 0.3s ease;
        }

        .game-card a:hover {
            background: white;
            transform: scale(1.05);
        }

        .dev-section {
            background: #fff5f5;
            padding: 25px;
            border-radius: 12px;
            border-left: 4px solid #fc8181;
        }

        .tech-stack {
            background: #f0fff4;
            padding: 15px 25px;
            border-radius: 8px;
            text-align: center;
            font-family: 'Monaco', monospace;
            font-size: 1.1em;
            color: #2d3748;
            margin: 20px 0;
            border: 2px solid #68d391;
        }

        .contact {
            text-align: center;
            margin: 30px 0;
        }

        .contact a {
            display: inline-block;
            padding: 12px 30px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-decoration: none;
            border-radius: 25px;
            font-size: 1.1em;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .contact a:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 20px rgba(102, 126, 234, 0.4);
        }

        .philosophy {
            background: #fffaf0;
            padding: 25px;
            border-radius: 12px;
            margin: 30px 0;
            border-left: 4px solid #ed8936;
        }

        .philosophy ul {
            list-style: none;
            padding-left: 0;
        }

        .philosophy li {
            padding: 8px 0;
            font-size: 1.1em;
        }

        .like-section {
            text-align: center;
            background: linear-gradient(135deg, #ffeaa7 0%, #fdcb6e 100%);
            padding: 40px;
            border-radius: 16px;
            margin: 40px 0;
        }

        .like-button {
            background: white;
            border: none;
            padding: 20px 40px;
            border-radius: 50px;
            font-size: 2em;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .like-button:hover {
            transform: scale(1.1);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }

        .like-button:active {
            transform: scale(0.95);
        }

        .like-button.liked {
            background: #ff6b6b;
            color: white;
            animation: pulse 0.3s ease;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        .like-count {
            font-size: 1.5em;
            font-weight: bold;
            color: #2d3748;
            margin-top: 20px;
        }

        .like-section p {
            margin-top: 15px;
            font-size: 1.2em;
            color: #2d3748;
        }

        .footer {
            text-align: center;
            padding: 30px;
            background: #f7fafc;
            border-radius: 12px;
            margin-top: 40px;
        }

        .footer .quote {
            font-style: italic;
            font-size: 1.3em;
            color: #4a5568;
            margin: 20px 0;
        }

        .footer .copyright {
            margin-top: 20px;
            color: #718096;
        }

        @media (max-width: 768px) {
            .container {
                padding: 30px 20px;
            }

            h2 {
                font-size: 1.6em;
            }

            .game-card {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>👋 嗨，我是 Torihiplay!</h1>
            <div class="subtitle">
                🎮 獨立遊戲開發者 | 來自台灣 🇹🇼
            </div>
        </div>

        <hr>

        <h2>🚀 關於我</h2>
        <div class="about-section">
            <pre>💻 職業: 獨立遊戲開發者
🌏 位置: 台灣 (Taiwan)
☕ 最愛: TAYAL×好咖·啡夢
🎯 目標: 創造有趣且令人難忘的遊戲體驗</pre>
        </div>

        <hr>

        <h2>🎮 我的遊戲作品</h2>

        <div class="game-card dino">
            <h3>1️⃣ DinoKite 🦖</h3>
            <h4>帶領小恐龍完成風箏夢想的可愛遊戲</h4>
            <p>經典的跑酷遊戲玩法，簡單卻令人上癮！控制可愛的小恐龍跳躍障礙物，挑戰你的反應速度和高分記錄。</p>
            <a href="https://apps.apple.com/tw/app/dinokite/id6741765553" target="_blank">📱 前往 App Store 下載</a>
        </div>

        <div class="game-card rolling">
            <h3>2️⃣ Rolling 🍎</h3>
            <h4>放置型水果莊園遊戲</h4>
            <p>輕鬆的放置型遊戲體驗，經營你的水果莊園！種植各種水果、收穫資源、擴展你的農場，享受休閒療癒的遊戲時光。</p>
            <a href="https://apps.apple.com/tw/app/rolling/id6742164718" target="_blank">📱 前往 App Store 下載</a>
        </div>

        <div class="game-card hopi">
            <h3>3️⃣ HopiIsland 🏝️</h3>
            <h4>小島冒險遊戲</h4>
            <p>踏上神秘小島的史詩冒險之旅！探索多樣化的區域，包括：</p>
            <ul>
                <li>🏰 <strong>王國系統</strong> - 在熱情的王國中闖蕩江湖</li>
                <li>☁️ <strong>空中小鎮</strong> - 漂浮在雲端的奇幻城市</li>
                <li>🎯 <strong>懸賞任務</strong> - 接受挑戰，獲得豐厚獎勵</li>
                <li>👑 <strong>皇家任務</strong> - 完成國王的特殊委託</li>
            </ul>
            <p>一個充滿探索、冒險與驚喜的開放世界等著你！</p>
            <a href="https://apps.apple.com/tw/app/hopisland/id6751443163" target="_blank">📱 前往 App Store 下載</a>
        </div>

        <hr>

        <h2>🔧 正在開發中</h2>
        <div class="dev-section">
            <h3>🍺 BeerAlarm</h3>
            <p><strong>新專案進行中...</strong></p>
            <p>敬請期待！更多資訊即將公開 🚀</p>
        </div>

        <hr>

        <h2>🛠️ 技術棧</h2>
        <div class="tech-stack">
            Unity | iOS Development | Xcode | Pixel Art | Game Design
        </div>

        <h2>🔗 聯繫方式</h2>
        <div class="contact">
            <a href="https://torihiplay.github.io/Torihiplay/" target="_blank">🌐 官方網站</a>
        </div>

        <hr>

        <h2>💡 關於我的遊戲</h2>
        <div class="philosophy">
            <p>我熱愛創造能帶給玩家快樂的遊戲體驗。從簡單的跑酷遊戲到複雜的冒險世界，每個專案都注入了我對遊戲開發的熱情。</p>
            <p><strong>設計理念：</strong></p>
            <ul>
                <li>✨ 簡單易懂的操作</li>
                <li>🎨 精美的視覺設計</li>
                <li>🎮 有趣且具挑戰性的玩法</li>
                <li>📱 優化的移動端體驗</li>
            </ul>
        </div>

        <hr>

        <h2>👍 給我一個讚！</h2>
        <div class="like-section">
            <p>如果你喜歡我的遊戲和專案，點擊下方按鈕給我一個讚吧！</p>
            <button class="like-button" id="likeBtn">
                <span id="likeIcon">👍</span>
                <span>按讚</span>
            </button>
            <div class="like-count">
                <span id="likeCount">0</span> 個讚
            </div>
            <p style="margin-top: 20px;">感謝每一位支持者！ 🎉</p>
        </div>

        <hr>

        <div class="footer">
            <div class="quote">💭 開發者的話</div>
            <p>"不用解釋，去感受它。"</p>
            <hr style="margin: 30px 0;">
            <p>⭐ 如果你喜歡我的遊戲，歡迎給個星星！</p>
            <div class="copyright">© 2024 Torihiplay | Made with ❤️ in Taiwan</div>
        </div>
    </div>

    <script>
        let likeCount = 0;
        let hasLiked = false;

        // 從 localStorage 讀取讚數
        if (localStorage.getItem('torihiplay_likes')) {
            likeCount = parseInt(localStorage.getItem('torihiplay_likes'));
            document.getElementById('likeCount').textContent = likeCount;
        }

        // 檢查用戶是否已經按過讚
        if (localStorage.getItem('torihiplay_user_liked') === 'true') {
            hasLiked = true;
            document.getElementById('likeBtn').classList.add('liked');
            document.getElementById('likeIcon').textContent = '❤️';
        }

        document.getElementById('likeBtn').addEventListener('click', function() {
            if (!hasLiked) {
                likeCount++;
                hasLiked = true;
                this.classList.add('liked');
                document.getElementById('likeIcon').textContent = '❤️';
                localStorage.setItem('torihiplay_likes', likeCount);
                localStorage.setItem('torihiplay_user_liked', 'true');
            } else {
                likeCount--;
                hasLiked = false;
                this.classList.remove('liked');
                document.getElementById('likeIcon').textContent = '👍';
                localStorage.setItem('torihiplay_likes', likeCount);
                localStorage.setItem('torihiplay_user_liked', 'false');
            }
            document.getElementById('likeCount').textContent = likeCount;
        });
    </script>
</body>
</html>
