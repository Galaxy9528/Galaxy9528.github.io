<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minecraft纯净服务器丨Java 1.21.4</title>
    <style>
        :root {
            --mc-dark: #1a1a1a;
            --mc-orange: #FF6B35;
            --mc-green: #5B8C5A;
            --mc-brown: #8B7355;
        }

        body {
            font-family: 'Microsoft YaHei', sans-serif;
            line-height: 1.8;
            margin: 0;
            padding: 20px;
            background: #0d0d0d;
            color: #e6e6e6;
        }

        .header-section {
            position: relative;
            background: rgba(30, 30, 30, 0.97);
            padding: 30px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: rgba(30, 30, 30, 0.97);
            padding: 0;
            border-radius: 10px;
        }

        h1 {
            color: var(--mc-orange);
            border-left: 5px solid var(--mc-green);
            padding-left: 15px;
            margin: 0 0 20px;
        }

        .version-box {
            background: rgba(255,107,53,0.1);
            padding: 20px;
            border-radius: 8px;
        }

        .feature-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            padding: 20px;
        }

        .feature-card {
            background: rgba(50,50,50,0.8);
            padding: 20px;
            border-radius: 8px;
            transition: transform 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-3px);
        }

        .rules-box {
            background: rgba(255,0,0,0.1);
            padding: 20px;
            margin: 20px;
            border-radius: 8px;
            column-count: 2;
        }

        .join-section {
            background: rgba(91,140,90,0.1);
            padding: 20px;
            margin: 20px;
            border-radius: 8px;
        }

        .form-link {
            display: inline-block;
            background: var(--mc-green);
            color: white !important;
            padding: 12px 30px;
            border-radius: 25px;
            text-decoration: none;
            margin: 15px 0 5px;
            transition: all 0.3s;
        }

        .form-link:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px rgba(91,140,90,0.4);
        }

        .city-description {
            background: rgba(60,145,230,0.1);
            padding: 20px;
            margin: 20px;
            border-radius: 8px;
        }

        .main-world-city {
            background: rgba(139,115,85,0.1);
            padding: 20px;
            margin: 20px;
            border-radius: 8px;
            border: 1px solid rgba(139,115,85,0.3);
            position: relative;
            padding-bottom: 60px;
        }

        .expand-button {
            position: absolute;
            bottom: 20px;
            right: 20px;
            background: var(--mc-green);
            color: white;
            padding: 8px 20px;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
            z-index: 1;
        }

        .expand-button:hover {
            background: #4A7B49;
            transform: scale(1.05);
        }

        .expand-button .arrow {
            font-size: 0.8em;
            transition: transform 0.3s;
        }

        .expand-button.active .arrow {
            transform: rotate(180deg);
        }

        .expanded-content {
            max-height: 0;
            opacity: 0;
            overflow: hidden;
            margin-top: 15px;
            padding: 0 15px;
            background: rgba(0,0,0,0.15);
            border-radius: 6px;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            transform: translateY(-10px);
            position: relative;
            z-index: 0;
        }

        .expanded-content.active {
            max-height: 500px;
            opacity: 1;
            padding: 15px;
            transform: translateY(0);
            transition-delay: 0.1s;
            margin-bottom: 40px;
        }

        .city-image {
            width: 100%;
            max-width: 800px;
            margin: 20px auto;
            display: block;
            border-radius: 8px;
            border: 2px solid rgba(255,255,255,0.1);
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .city-image:hover {
            transform: scale(1.02);
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
        }

        .image-caption {
            text-align: center;
            color: #aaa;
            margin-top: 10px;
            font-size: 0.9em;
        }

        /* 图片轮播组件样式 */
        .image-carousel {
            position: relative;
            max-width: 800px;
            margin: 20px auto;
            overflow: hidden;
            border-radius: 8px;
            border: 2px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }

        .carousel-container {
            display: flex;
            transition: transform 0.5s ease-in-out;
        }

        .carousel-image {
            width: 100%;
            flex-shrink: 0;
            border-radius: 8px;
        }

        .carousel-button {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0, 0, 0, 0.5);
            color: white;
            border: none;
            padding: 10px;
            cursor: pointer;
            border-radius: 50%;
            font-size: 18px;
            transition: background 0.3s;
        }

        .carousel-button:hover {
            background: rgba(0, 0, 0, 0.8);
        }

        .carousel-button.prev {
            left: 10px;
        }

        .carousel-button.next {
            right: 10px;
        }

        @media (max-width: 768px) {
            .feature-grid {
                grid-template-columns: 1fr;
            }
            .rules-box {
                column-count: 1;
            }
            .header-section {
                padding: 20px;
            }
            .expand-button {
                bottom: 10px;
                right: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header-section">
            <h1>Minecraft纯净服务器</h1>
            <div class="version-box">
                <p>当前版本：Java版 1.21.4</p>
                <p>兼容版本：1.20.x - 1.21.4（建议使用最新版）</p>
                <p>类型：原版生存丨自由建造丨社区协作丨长期更新</p>
            </div>
        </div>

        <div class="feature-grid">
            <div class="feature-card">
                <h2>🌟 100% 原版体验</h2>
                <ul>
                    <li>完全无插件、无魔改，保留原汁原味的生存挑战</li>
                    <li>支持1.20-1.21.4版本自由加入</li>
                    <li>同步官方最新内容更新</li>
                </ul>
            </div>

            <div class="feature-card">
                <h2>⏳ 长期稳定发展</h2>
                <ul>
                    <li>自2025年2月开服地图永不重置</li>
                    <li>玩家建筑永久保存</li>
                    <li>三界全维度开放</li>
                </ul>
            </div>

            <div class="feature-card">
                <h2>⚡ 极致性能优化</h2>
                <ul>
                    <li>专业级服务器硬件</li>
                    <li>TPS常年保持20+</li>
                    <li>自动备份+智能防护</li>
                </ul>
            </div>
        </div>

        <div class="rules-box">
            <h2>服务器规则</h2>
            <ul>
                <li>禁止外挂/X-Ray等作弊行为</li>
                <li>禁止破坏/盗窃他人财产</li>
                <li>禁止广告/引战/刷屏</li>
                <li>违者视情况封禁处理</li>
            </ul>
        </div>

        <div class="join-section">
            <h2>如何加入？</h2>
            <ul>
                <li>加DY群获取审核表单</li>
                <li>完整填写入服申请</li>
                <li>48小时内邮件发送服务器IP</li>
            </ul>
            <a href="https://www.wjx.cn/vm/OAfb7GX.aspx#" 
               class="form-link"
               target="_blank"
               rel="noopener">
               📝 立即填写审核表单
            </a>
        </div>

        <div class="main-world-city">
            <h2>主世界主城</h2>
            <p>服务器的主世界主城，是一座空中悬浮的中式风格建筑。整体由多座塔楼相连构成，主塔楼居于中央，高耸且层次分明，飞檐翘角极具特色。四周分布着稍矮的塔楼，与主塔楼相互呼应，共同形成错落有致的天际线。</p>
            <p>建筑以深棕色和白色为主色调，辅以灰色石块作为基底，古朴又庄重。外部，橙红色的灯笼沿着屋檐和走廊密集悬挂，在夜间散发暖光，增添温馨氛围。墙面上，方形的窗户有序排列，透出柔和光线。</p>
            <p>内部大厅宽敞，木质立柱粗壮，支撑起高高的天花板。天花板装饰有复杂的几何图案，搭配绿色方块点缀，如同繁茂枝叶。地面由不同色调的方块拼接，形成丰富纹理。大厅两侧设有长桌和座椅，前方还有类似祭台的结构。</p>
            <p>主城边缘环绕着水流和绿植，水面漂浮着荷叶，增添生机。整座主城悬浮于夜空之中，背后是深邃的天幕和闪烁繁星，充满神秘梦幻之感。</p>

            <!-- 展开按钮 -->
            <div class="expand-button" onclick="toggleExpand()">
                <span class="button-text">详情</span>
                <span class="arrow">▼</span>
            </div>

            <!-- 展开内容 -->
            <div class="expanded-content" id="expandedContent">
                <p>主世界主城下方还附带工业区和住宅区，工业区有树厂，刷石机村民交易所，服务器仓库，指令中心和贵重物品仓库等。住宅区拥有多种建筑选择，有靠近河岸的别墅，有冰湖上的小屋，有位居下方的小别墅和地底别墅，同时还有山地别墅。最后的最后末地大厅和末地入口是附带刷沙机的，所以不要自己建。</p>
            </div>

            <!-- 主世界主城图片轮播组件 -->
            <div class="image-carousel">
                <div class="carousel-container">
                    <img src="https://img.picui.cn/free/2025/03/19/67da2e270d2e9.png" alt="主世界主城图片 1" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da2e28aa941.png" alt="主世界主城图片 2" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da2e2e33907.png" alt="主世界主城图片 3" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da2e2fd8206.png" alt="主世界主城图片 4" class="carousel-image">
                </div>
                <button class="carousel-button prev" onclick="prevImage('main-world')">❮</button>
                <button class="carousel-button next" onclick="nextImage('main-world')">❯</button>
            </div>
            <div class="image-caption">主世界主城实景截图（点击左右按钮切换图片）</div>
        </div>

        <div class="city-description">
            <h2>末地主城</h2>
            <p>服务器的末地主城外观极具科幻感与未来感。整体建筑以黑白为主色调，搭配亮眼的橙色装饰，形成强烈视觉冲击。</p>
            <p>主城结构错综复杂，由大量几何形状模块拼接而成。从空中俯瞰，中心是巨大的圆形构造，如能量核心般散发着橙色光芒，向外辐射出多条类似机械臂的建筑分支，布满精密的结构和装置，仿佛随时会启动运转。</p>
            <p>建筑外部，巨大的框架和延伸的平台相互交错，部分区域悬空，给人以悬浮之感。走进其中，通道和房间相连，天花板和墙壁上分布着发光条纹和方块，照亮内部空间。有的区域像是大型工厂，林立着高耸的机械柱和管道；有的则类似指挥中心，有着开阔的视野和复杂的操控台外观。</p>
            <p>主城背景是浩瀚星空，远处的行星在光影渲染下更显神秘，与末地主城的科技风外观相映衬，仿佛是宇宙中的一座神秘堡垒。</p>

            <!-- 末地主城图片轮播组件 -->
            <div class="image-carousel">
                <div class="carousel-container">
                    <img src="https://img.picui.cn/free/2025/03/19/67da1339afa56.png" alt="末地主城图片 1" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da133ec82b7.png" alt="末地主城图片 2" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da1336a2e16.png" alt="末地主城图片 3" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da133e40a41.png" alt="末地主城图片 4" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da133e882a7.png" alt="末地主城图片 5" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da133fe58a0.png" alt="末地主城图片 6" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/03/19/67da13431ee52.png" alt="末地主城图片 7" class="carousel-image">
                </div>
                <button class="carousel-button prev" onclick="prevImage('end-city')">❮</button>
                <button class="carousel-button next" onclick="nextImage('end-city')">❯</button>
            </div>
            <div class="image-caption">末地主城实景截图（点击左右按钮切换图片）</div>
        </div>
    </div>

    <script>
        // 展开/收起功能
        function toggleExpand() {
            const button = document.querySelector('.expand-button');
            const buttonText = button.querySelector('.button-text');
            const content = document.getElementById('expandedContent');
            
            button.classList.toggle('active');
            content.classList.toggle('active');
            
            if (button.classList.contains('active')) {
                buttonText.textContent = '收起';
            } else {
                buttonText.textContent = '详情';
            }
            
            if(content.classList.contains('active')) {
                const offset = button.offsetHeight + 20;
                content.scrollIntoView({
                    behavior: 'smooth',
                    block: 'start'
                });
                
                window.scrollBy({
                    top: -offset,
                    behavior: 'smooth'
                });
            }
        }

        // 图片轮播功能
        const carousels = {
            'main-world': {
                currentIndex: 0,
                container: document.querySelector('.main-world-city .carousel-container'),
                images: document.querySelectorAll('.main-world-city .carousel-image')
            },
            'end-city': {
                currentIndex: 0,
                container: document.querySelector('.city-description .carousel-container'),
                images: document.querySelectorAll('.city-description .carousel-image')
            }
        };

        function showImage(carouselId, index) {
            const carousel = carousels[carouselId];
            const offset = -index * 100;
            carousel.container.style.transform = `translateX(${offset}%)`;
        }

        function nextImage(carouselId) {
            const carousel = carousels[carouselId];
            if (carousel.currentIndex === carousel.images.length - 1) {
                carousel.currentIndex = 0;
                carousel.container.style.transition = 'none';
                showImage(carouselId, carousel.currentIndex);
                void carousel.container.offsetWidth; // 强制重绘
                carousel.container.style.transition = 'transform 0.5s ease-in-out';
            } else {
                carousel.currentIndex++;
                showImage(carouselId, carousel.currentIndex);
            }
        }

        function prevImage(carouselId) {
            const carousel = carousels[carouselId];
            if (carousel.currentIndex === 0) {
                carousel.currentIndex = carousel.images.length - 1;
                carousel.container.style.transition = 'none';
                showImage(carouselId, carousel.currentIndex);
                void carousel.container.offsetWidth; // 强制重绘
                carousel.container.style.transition = 'transform 0.5s ease-in-out';
            } else {
                carousel.currentIndex--;
                showImage(carouselId, carousel.currentIndex);
            }
        }

        // 初始化
        showImage('main-world', 0);
        showImage('end-city', 0);
    </script>
</body>
</html>
