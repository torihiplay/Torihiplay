<!DOCTYPE html>
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
            background: linear-gradient(135deg, #2c1810 0%, #1a0f08 100%);
            padding: 40px;
            border-radius: 16px;
            margin: 40px 0;
            position: relative;
            overflow: hidden;
        }

        .like-section p {
            font-size: 1.2em;
            color: #ffa07a;
            margin-bottom: 20px;
        }

        #fireCanvas {
            display: block;
            margin: 20px auto;
            border-radius: 10px;
        }

        .wood-pile {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }

        .wood {
            background: linear-gradient(135deg, #8b4513 0%, #a0522d 50%, #8b4513 100%);
            border-radius: 12px;
            cursor: pointer;
            transition: transform 0.2s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
            position: relative;
            border: 2px solid #654321;
        }

        .wood.small {
            width: 60px;
            height: 20px;
        }

        .wood.medium {
            width: 80px;
            height: 25px;
        }

        .wood.large {
            width: 100px;
            height: 30px;
        }

        .wood::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 10%;
            right: 10%;
            height: 2px;
            background: #654321;
            opacity: 0.5;
        }

        .wood:hover {
            transform: scale(1.1);
        }

        .wood:active {
            transform: scale(0.95);
        }

        .wood.throwing {
            position: fixed;
            z-index: 1000;
            pointer-events: none;
        }

        .plus-one {
            position: absolute;
            font-size: 2em;
            font-weight: bold;
            color: #ff6347;
            text-shadow: 0 0 10px #ff6347;
            pointer-events: none;
            animation: floatUp 1s ease-out forwards;
        }

        @keyframes floatUp {
            0% {
                opacity: 1;
                transform: translateY(0);
            }
            100% {
                opacity: 0;
                transform: translateY(-80px);
            }
        }

        .fire-count {
            font-size: 1.5em;
            font-weight: bold;
            color: #ffa07a;
            margin-top: 20px;
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

        <h2>🔥 添柴加火！</h2>
        <div class="like-section">
            <p>點擊下方的木頭投入火堆，讓火焰燒得更旺！</p>
            <canvas id="fireCanvas" width="300" height="200"></canvas>
            <div class="fire-count">
                🔥 已投入 <span id="woodCount">0</span> 根木頭
            </div>
            <div class="wood-pile">
                <div class="wood small" onclick="throwWood(this, 1)"></div>
                <div class="wood medium" onclick="throwWood(this, 1.5)"></div>
                <div class="wood large" onclick="throwWood(this, 2)"></div>
            </div>
            <p style="margin-top: 20px; color: #ffa07a;">讓我們一起讓這把火燒得更旺！ 🔥</p>
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
        // 火焰系統
        const canvas = document.getElementById('fireCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        let fireIntensity = 1;
        let woodCount = 0;

        class FireParticle {
            constructor(x, y, intensity = 1) {
                this.x = x;
                this.y = y;
                this.vx = (Math.random() - 0.5) * 2 * intensity;
                this.vy = -Math.random() * 3 * intensity - 1;
                this.life = Math.random() * 60 + 40;
                this.maxLife = this.life;
                this.size = Math.random() * 8 * intensity + 2;
            }

            update() {
                this.x += this.vx;
                this.y += this.vy;
                this.vy -= 0.1;
                this.life--;
                this.size *= 0.97;
            }

            draw() {
                const alpha = this.life / this.maxLife;
                const lifeRatio = this.life / this.maxLife;
                
                // 根據火焰強度改變顏色
                let r, g, b;
                
                // 當火焰很旺時（強度>2），加入藍色/白色
                if (fireIntensity > 2.5) {
                    // 超高溫 - 藍白火焰
                    if (lifeRatio > 0.7) {
                        r = 200 + Math.floor(55 * lifeRatio);
                        g = 220 + Math.floor(35 * lifeRatio);
                        b = Math.floor(255 * (fireIntensity - 2.5) / 1.5);
                    } else if (lifeRatio > 0.5) {
                        r = 255;
                        g = 255;
                        b = Math.floor(200 * (fireIntensity - 2.5) / 1.5);
                    } else {
                        r = 255;
                        g = Math.floor(150 + lifeRatio * 105);
                        b = 0;
                    }
                } else if (fireIntensity > 2) {
                    // 高溫 - 白黃火焰
                    if (lifeRatio > 0.6) {
                        r = 255;
                        g = Math.floor(200 + (lifeRatio - 0.6) * 137);
                        b = Math.floor(100 * (fireIntensity - 2) / 0.5);
                    } else {
                        r = 255;
                        g = Math.floor(150 + lifeRatio * 105);
                        b = 0;
                    }
                } else if (fireIntensity > 1.5) {
                    // 中高溫 - 橙黃火焰
                    if (lifeRatio > 0.6) {
                        r = 255;
                        g = Math.floor(180 + (lifeRatio - 0.6) * 187);
                        b = 0;
                    } else {
                        r = 255;
                        g = Math.floor(120 + lifeRatio * 135);
                        b = 0;
                    }
                } else {
                    // 正常溫度 - 紅橙火焰
                    if (lifeRatio > 0.6) {
                        r = 255;
                        g = Math.floor(100 + (lifeRatio - 0.6) * 387);
                        b = 0;
                    } else {
                        r = 255;
                        g = Math.floor(69 + lifeRatio * 150);
                        b = 0;
                    }
                }

                ctx.fillStyle = `rgba(${r}, ${g}, ${b}, ${alpha})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();

                // 內核發光效果 - 根據強度調整
                if (lifeRatio > 0.5) {
                    const coreIntensity = fireIntensity > 2 ? 0.8 : 0.5;
                    const coreColor = fireIntensity > 2.5 ? '200, 220, 255' : '255, 255, 150';
                    ctx.fillStyle = `rgba(${coreColor}, ${alpha * coreIntensity})`;
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.size * 0.5, 0, Math.PI * 2);
                    ctx.fill();
                }
            }

            isDead() {
                return this.life <= 0;
            }
        }

        function createFireParticles() {
            const particlesPerFrame = Math.floor(5 * fireIntensity);
            for (let i = 0; i < particlesPerFrame; i++) {
                const x = canvas.width / 2 + (Math.random() - 0.5) * 60;
                const y = canvas.height - 20;
                particles.push(new FireParticle(x, y, fireIntensity));
            }
        }

        function animate() {
            ctx.fillStyle = 'rgba(44, 24, 16, 0.3)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            createFireParticles();

            particles = particles.filter(p => !p.isDead());
            particles.forEach(p => {
                p.update();
                p.draw();
            });

            // 火焰強度慢慢衰減
            if (fireIntensity > 1) {
                fireIntensity *= 0.99;
            }

            requestAnimationFrame(animate);
        }

        function boostFire(multiplier = 1.5) {
            fireIntensity = Math.min(fireIntensity + multiplier, 4);
        }

        function showPlusOne(size) {
            const section = document.querySelector('.like-section');
            const plusOne = document.createElement('div');
            plusOne.className = 'plus-one';
            plusOne.textContent = '+' + Math.round(size);
            plusOne.style.left = `${canvas.offsetLeft + canvas.width / 2 - 20}px`;
            plusOne.style.top = `${canvas.offsetTop + 50}px`;
            section.appendChild(plusOne);

            setTimeout(() => plusOne.remove(), 1000);
        }

        function throwWood(woodElement, multiplier = 1.5) {
            // 增加計數
            woodCount++;
            document.getElementById('woodCount').textContent = woodCount;

            // 複製木頭用於動畫
            const wood = woodElement.cloneNode(true);
            wood.classList.add('throwing');
            document.body.appendChild(wood);

            // 獲取起始和目標位置
            const rect = woodElement.getBoundingClientRect();
            const canvasRect = canvas.getBoundingClientRect();
            
            const startX = rect.left;
            const startY = rect.top;
            const endX = canvasRect.left + canvasRect.width / 2 - rect.width / 2;
            const endY = canvasRect.top + canvasRect.height / 2;

            wood.style.left = startX + 'px';
            wood.style.top = startY + 'px';

            // 拋物線動畫
            const duration = 800;
            const startTime = Date.now();

            function animateThrow() {
                const elapsed = Date.now() - startTime;
                const progress = Math.min(elapsed / duration, 1);

                // 使用二次貝塞爾曲線模擬拋物線
                const controlY = startY - 150;
                const t = progress;
                const x = startX + (endX - startX) * t;
                const y = (1 - t) * (1 - t) * startY + 2 * (1 - t) * t * controlY + t * t * endY;

                wood.style.left = x + 'px';
                wood.style.top = y + 'px';
                wood.style.transform = `rotate(${progress * 720}deg)`;

                if (progress < 1) {
                    requestAnimationFrame(animateThrow);
                } else {
                    wood.remove();
                    boostFire(multiplier);
                    showPlusOne(multiplier);
                }
            }

            animateThrow();
        }

        // 開始動畫
        animate();
    </script>
</body>
</html>
