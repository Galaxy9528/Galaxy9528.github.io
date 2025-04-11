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
            display: flex;
            align-items: center;
            justify-content: space-between;
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
            margin: 0;
        }

        .version-box {
            background: rgba(255,107,53,0.1);
            /* 修改此处的内边距以调整宽度 */
            padding: 10px; 
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
            position: relative;
            padding-bottom: 60px;
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

        /* 新闻快讯区域样式 */
        .news-section {
            background: url('https://img.picui.cn/free/2025/04/09/67f649ebb7b88.png') no-repeat center center / cover;
            opacity: 1.0;
            padding: 20px;
            margin: 20px;
            border-radius: 8px;
        }

        /* 联系我们区域样式 */
        .contact-section {
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            margin: 20px;
            border-radius: 8px;
            text-align: center; /* 文字居中 */
        }

        /* 语言按钮样式 */
        .language-button {
            background: var(--mc-green);
            color: white;
            padding: 8px 20px;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .language-button:hover {
            background: #4A7B49;
            transform: scale(1.05);
        }

        .language-options {
            position: absolute;
            top: calc(100% + 10px);
            right: 0;
            background: rgba(30, 30, 30, 0.97);
            border-radius: 8px;
            padding: 10px;
            flex-direction: column;
            opacity: 0;
            transform: translateY(-10px);
            transition: all 0.3s ease;
            pointer-events: none;
        }

        .language-options.show {
            opacity: 1;
            transform: translateY(0);
            pointer-events: auto;
        }

        .language-option {
            cursor: pointer;
            padding: 5px 10px;
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
            <h1 data-lang="zh">Minecraft纯净服务器</h1>
            <h1 data-lang="en" style="display: none;">Minecraft Vanilla Server</h1>
            <button class="language-button" onclick="toggleLanguageOptions()">语言/language</button>
            <div class="language-options" id="languageOptions">
                <div class="language-option" onclick="changeLanguage('zh')">中文</div>
                <div class="language-option" onclick="changeLanguage('en')">English</div>
            </div>
        </div>

        <div class="version-box">
            <p data-lang="zh">当前版本：Java版 1.21.4</p>
            <p data-lang="en" style="display: none;">Current Version: Java Edition 1.21.4</p>
            <p data-lang="zh">兼容版本：1.20.x - 1.21.4（建议使用最新版）</p>
            <p data-lang="en" style="display: none;">Compatible Versions: 1.20.x - 1.21.4 (It is recommended to use the latest version)</p>
            <p data-lang="zh">类型：原版生存丨自由建造丨社区协作丨长期更新</p>
            <p data-lang="en" style="display: none;">Type: Vanilla Survival | Free Building | Community Collaboration | Long - term Updates</p>
        </div>

        <div class="feature-grid">
            <div class="feature-card">
                <h2 data-lang="zh">🌟 100% 原版体验</h2>
                <h2 data-lang="en" style="display: none;">🌟 100% Vanilla Experience</h2>
                <ul>
                    <li data-lang="zh">完全无插件、无魔改，保留原汁原味的生存挑战</li>
                    <li data-lang="en" style="display: none;">Completely plugin - free and unmodified, retaining the original survival challenges</li>
                    <li data-lang="zh">支持1.20.x-1.21.x版本自由加入</li>
                    <li data-lang="en" style="display: none;">Supports free joining from versions 1.20 - 1.21.4</li>
                    <li data-lang="zh">同步官方最新内容更新</li>
                    <li data-lang="en" style="display: none;">Synchronizes with the latest official content updates</li>
                </ul>
            </div>

            <div class="feature-card">
                <h2 data-lang="zh">⏳ 长期稳定发展</h2>
                <h2 data-lang="en" style="display: none;">⏳ Long - term Stable Development</h2>
                <ul>
                    <li data-lang="zh">自2025年2月开服地图永不重置(除非突发情况)</li>
                    <li data-lang="en" style="display: none;">The server map has never been reset since it opened in February 2025 and will never be reset</li>
                    <li data-lang="zh">玩家建筑永久保存</li>
                    <li data-lang="en" style="display: none;">Players' buildings are permanently preserved</li>
                    <li data-lang="zh">三界全维度开放</li>
                    <li data-lang="en" style="display: none;">All dimensions of the three realms are open</li>
                </ul>
            </div>

            <div class="feature-card">
                <h2 data-lang="zh">⚡ 极致性能优化</h2>
                <h2 data-lang="en" style="display: none;">⚡ Extreme Performance Optimization</h2>
                <ul>
                    <li data-lang="zh">专业级服务器硬件</li>
                    <li data-lang="en" style="display: none;">Professional - grade server hardware</li>
                    <li data-lang="zh">TPS常年保持20+</li>
                    <li data-lang="en" style="display: none;">TPS remains above 20 all year round</li>
                    <li data-lang="zh">自动备份+智能防护</li>
                    <li data-lang="en" style="display: none;">Automatic backup + intelligent protection</li>
                </ul>
            </div>
        </div>

        <div class="rules-box">
            <h2 data-lang="zh">服务器规则</h2>
            <h2 data-lang="en" style="display: none;">Server Rules</h2>
            <ul>
                <li data-lang="zh">禁止外挂/X-Ray等作弊行为</li>
                <li data-lang="en" style="display: none;">Cheating behaviors such as using hacks or X - Ray are prohibited</li>
                <li data-lang="zh">禁止破坏/盗窃他人财产</li>
                <li data-lang="en" style="display: none;">Destroying or stealing others' property is prohibited</li>
                <li data-lang="zh">禁止广告/引战/刷屏</li>
                <li data-lang="en" style="display: none;">Advertising, inciting fights, and spamming are prohibited</li>
                <li data-lang="zh">违者视情况封禁处理</li>
                <li data-lang="en" style="display: none;">Violators will be banned depending on the situation</li>
            </ul>
        </div>

        <div class="join-section">
            <h2 data-lang="zh">如何加入？</h2>
            <h2 data-lang="en" style="display: none;">How to Join?</h2>
            <ul>
                <li data-lang="zh">加抖音群获取审核表单</li>
                <li data-lang="en" style="display: none;">Join the Tik Tok (china) group to get the review form</li>
                <li data-lang="zh">完整填写入服申请</li>
                <li data-lang="en" style="display: none;">Fill out the server application form completely</li>
                <li data-lang="zh">48小时内邮件发送服务器IP</li>
                <li data-lang="en" style="display: none;">The server IP will be sent via email within 48 hours</li>
            </ul>
            <a href="https://www.wjx.cn/vm/OAfb7GX.aspx#" 
               class="form-link"
               target="_blank"
               rel="noopener">
               <span data-lang="zh">📝 立即填写审核表单</span>
               <span data-lang="en" style="display: none;">📝 Fill out the review form immediately</span>
            </a>
        </div>

        <!-- 新闻快讯区域 -->
        <div class="news-section">
            <h2 data-lang="zh">服务器新闻快讯(不定时更新)</h2>
            <h2 data-lang="en" style="display: none;">Server News Flash</h2>
            <p data-lang="zh">目前服务器的白名单已添加完成,存档也以更换,目前正在试运行(运行时间2周)</p>
            <p data-lang="en" style="display: none;">Due to the frequent appearance of 666JJY (a server - crashing person), the server owner has decided to implement a whitelist system and is gradually replacing the game save and the server's properties.</p>
        </div>

        <div class="main-world-city">
            <h2 data-lang="zh">主世界主城</h2>
            <h2 data-lang="en" style="display: none;">Main World Capital City</h2>
            <p data-lang="zh">服务器的主世界主城，是一座空中悬浮的中式风格建筑。整体由多座塔楼相连构成，主塔楼居于中央，高耸且层次分明，飞檐翘角极具特色。四周分布着稍矮的塔楼，与主塔楼相互呼应，共同形成错落有致的天际线。</p>
            <p data-lang="en" style="display: none;">The main world capital city of the server is a Chinese - style building floating in the air. It is composed of multiple connected towers. The main tower is located in the center, tall and well - structured, with distinctive upturned eaves and corners. There are slightly shorter towers distributed around it, echoing the main tower and together forming a well - arranged skyline.</p>
            <p data-lang="zh">建筑以深棕色和白色为主色调，辅以灰色石块作为基底，古朴又庄重。外部，橙红色的灯笼沿着屋檐和走廊密集悬挂，在夜间散发暖光，增添温馨氛围。墙面上，方形的窗户有序排列，透出柔和光线。</p>
            <p data-lang="en" style="display: none;">The building mainly features dark brown and white colors, with grey stones as the base, looking simple and solemn. Outside, orange - red lanterns are densely hung along the eaves and corridors, emitting warm light at night and adding a warm atmosphere. Square windows are neatly arranged on the walls, letting out soft light.</p>
            <p data-lang="zh">内部大厅宽敞，木质立柱粗壮，支撑起高高的天花板。天花板装饰有复杂的几何图案，搭配绿色方块点缀，如同繁茂枝叶。地面由不同色调的方块拼接，形成丰富纹理。大厅两侧设有长桌和座椅，前方还有类似祭台的结构。</p>
            <p data-lang="en" style="display: none;">The interior hall is spacious, with thick wooden columns supporting the high ceiling. The ceiling is decorated with complex geometric patterns and dotted with green blocks, resembling lush foliage. The floor is made up of blocks of different colors, creating a rich texture. There are long tables and chairs on both sides of the hall, and there is also an altar - like structure in the front.</p>
            <p data-lang="zh">主城边缘环绕着水流和绿植，水面漂浮着荷叶，增添生机。整座主城悬浮于夜空之中，背后是深邃的天幕和闪烁繁星，充满神秘梦幻之感。</p>
            <p data-lang="en" style="display: none;">The edge of the capital city is surrounded by water and green plants. Lotus leaves float on the water surface, adding vitality. The entire capital city floats in the night sky, with a deep sky and twinkling stars in the background, full of mystery and fantasy.</p>

            <!-- 展开按钮 -->
            <div class="expand-button" onclick="toggleExpand('main-world')">
                <span data-lang="zh" class="button-text">详情</span>
                <span data-lang="en" style="display: none;" class="button-text">Details</span>
                <span class="arrow">▼</span>
            </div>

            <!-- 展开内容 -->
            <div class="expanded-content" id="main-world-expandedContent">
                <p data-lang="zh">主世界主城下方还附带工业区和住宅区，工业区有树厂，刷石机村民交易所，服务器仓库，指令中心和贵重物品仓库等。住宅区拥有多种建筑选择，有靠近河岸的别墅，有冰湖上的小屋，有位居下方的小别墅和地底别墅，同时还有山地别墅。最后的最后末地大厅和末地入口是附带刷沙机的，所以不要自己建。</p>
                <p data-lang="en" style="display: none;">There are also industrial and residential areas below the main world capital city. The industrial area has a tree farm, a stone generator, a villager trading post, a server warehouse, a command center, and a valuable items warehouse. The residential area offers a variety of building options, including villas near the river, cabins on the ice lake, small villas below, underground villas, and mountain villas. Finally, the end hall and the end entrance come with a sand generator, so don't build your own.</p>
            </div>

            <!-- 主世界主城图片轮播组件 -->
            <div class="image-carousel">
                <div class="carousel-container">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4ffc0e5d2d.png" alt="主世界主城图片 1" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4ffc12feec.png" alt="主世界主城图片 2" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4ffc50ef98.png" alt="主世界主城图片 3" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4ffc6d0960.png" alt="主世界主城图片 4" class="carousel-image">
                </div>
                <button class="carousel-button prev" onclick="prevImage('main-world')">❮</button>
                <button class="carousel-button next" onclick="nextImage('main-world')">❯</button>
            </div>
            <div class="image-caption">
                <span data-lang="zh">主世界主城实景截图（点击左右按钮切换图片）</span>
                <span data-lang="en" style="display: none;">Real - life screenshots of the main world capital city (Click the left and right buttons to switch images)</span>
            </div>
        </div>

        <div class="city-description">
            <h2 data-lang="zh">末地主城</h2>
            <h2 data-lang="en" style="display: none;">End Capital City</h2>
            <p data-lang="zh">服务器的末地主城外观极具科幻感与未来感。整体建筑以黑白为主色调，搭配亮眼的橙色装饰，形成强烈视觉冲击。</p>
            <p data-lang="en" style="display: none;">The appearance of the end capital city of the server is full of science - fiction and futuristic feelings. The overall building mainly features black and white colors, paired with eye - catching orange decorations, creating a strong visual impact.</p>
            <p data-lang="zh">主城结构错综复杂，由大量几何形状模块拼接而成。从空中俯瞰，中心是巨大的圆形构造，如能量核心般散发着橙色光芒，向外辐射出多条类似机械臂的建筑分支，布满精密的结构和装置，仿佛随时会启动运转。</p>
            <p data-lang="en" style="display: none;">The structure of the capital city is complex, composed of a large number of geometric - shaped modules. When viewed from above, the center is a huge circular structure, emitting orange light like an energy core, and radiating multiple building branches like mechanical arms, filled with precise structures and devices, as if it could start operating at any time.</p>
            <p data-lang="zh">建筑外部，巨大的框架和延伸的平台相互交错，部分区域悬空，给人以悬浮之感。走进其中，通道和房间相连，天花板和墙壁上分布着发光条纹和方块，照亮内部空间。有的区域像是大型工厂，林立着高耸的机械柱和管道；有的则类似指挥中心，有着开阔的视野和复杂的操控台外观。</p>
            <p data-lang="en" style="display: none;">Outside the building, huge frames and extended platforms are intertwined, with some areas suspended in the air, giving a sense of floating. Inside, passages and rooms are connected, and there are glowing stripes and blocks on the ceiling and walls, illuminating the interior space. Some areas resemble large factories, with tall mechanical columns and pipes standing; others are similar to command centers, with a wide view and a complex console appearance.</p>
            <p data-lang="zh">主城背景是浩瀚星空，远处的行星在光影渲染下更显神秘，与末地主城的科技风外观相映衬，仿佛是宇宙中的一座神秘堡垒。</p>
            <p data-lang="en" style="display: none;">The background of the capital city is the vast starry sky. The distant planets appear more mysterious under the light and shadow rendering, contrasting with the technological appearance of the end capital city, as if it were a mysterious fortress in the universe.</p>

            <!-- 末地主城图片轮播组件 -->
            <div class="image-carousel">
                <div class="carousel-container">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4fd51d5d91.png" alt="末地主城图片 1" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4fd536c51e.png" alt="末地主城图片 2" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4fd5392cb4.png" alt="末地主城图片 3" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4fd57af068.png" alt="末地主城图片 4" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4fd57b8f72.png" alt="末地主城图片 5" class="carousel-image">
                    <img src="https://img.picui.cn/free/2025/04/08/67f4fd5cac567.png" alt="末地主城图片 6" class="carousel-image">
                </div>
                <button class="carousel-button prev" onclick="prevImage('end-city')">❮</button>
                <button class="carousel-button next" onclick="nextImage('end-city')">❯</button>
            </div>
            <div class="image-caption">
                <span data-lang="zh">末地主城实景截图（点击左右按钮切换图片）</span>
                <span data-lang="en" style="display: none;">Real - life screenshots of the end capital city (Click the left and right buttons to switch images)</span>
            </div>

            <!-- 展开按钮 -->
            <div class="expand-button" onclick="toggleExpand('end-city')">
                <span data-lang="zh" class="button-text">详情</span>
                <span data-lang="en" style="display: none;" class="button-text">Details</span>
                <span class="arrow">▼</span>
            </div>

            <!-- 展开内容 -->
            <div class="expanded-content" id="end-city-expandedContent">
                <p data-lang="zh">末地主城是服务器里一个比较特殊的建筑，因为这个建筑是我们的Obscurus_他花钱去买的，然后建了也有比较长的时间，然后是加上我记得因该是代有混凝土固化机的(我忘了)然后附近的外岛也是有装饰的，然后建筑大部分来源于B站的咸到老时变成鱼，末地的建筑基本上都是他的。</p>
                <p data-lang="en" style="display: none;">The end capital city is a relatively special building in the server. This building was bought by our Obscurus_ with money, and it has been built for a relatively long time. I remember it should have a concrete solidifier (I forgot). The nearby outer islands are also decorated. Most of the buildings in the end come from Xianlaodao when he turns into a fish on Bilibili. Most of the end buildings are his.</p>
            </div>
        </div>

        <!-- 联系我们区域 -->
<div class="contact-section">
    <h2 data-lang="zh">联系我们</h2>
    <h2 data-lang="en" style="display: none;">Contact Us</h2>
    <p data-lang="zh">工作邮箱：daqi.zhan.2030@students.avenueschina.cn，nature.gao.2030@students.avenueschina.cn,william.sima.2030@students.avenueschina.cn</p>
    <p data-lang="en" style="display: none;">Work Email: daqi.zhan.2030@students.avenueschina.cn,nature.gao.2030@students.avenueschina.cn,
        william.sima.2030@students.avenueschina.cn</p>
    <p data-lang="zh">个人邮箱：william20120210@163.com,nature.minecraftwrold@gmail.com</p>
    <p data-lang="en" style="display: none;">Personal Email: william20120210@163.com,nature.minecraftwrold@gmail.com</p>
    <p data-lang="zh">B站搜索：狂笑的猫酱学长</p>
    <p data-lang="en" style="display: none;">Search on Bilibili:狂笑的猫酱学长</p>
</div>
</div>
<!-- 底部区域 -->
<footer class="bg-gray-900 text-white py-8">
    <div class="container mx-auto text-center">
        <p data-lang="zh">&copy; 2025 Minecraft纯净服务器. 保留所有权利.</p>
        <p data-lang="en" style="display: none;">&copy; 2025 Minecraft Pure Server. All rights reserved.</p>
        <div class="flex justify-center space-x-4 mt-4">
            <a href="#" target="_blank" rel="noopener noreferrer" data-lang="zh">隐私政策</a>
            <a href="#" target="_blank" rel="noopener noreferrer" data-lang="en" style="display: none;">Privacy Policy</a>
            <a href="#" target="_blank" rel="noopener noreferrer" data-lang="zh">使用条款</a>
            <a href="#" target="_blank" rel="noopener noreferrer" data-lang="en" style="display: none;">Terms of Use</a>
        </div>
        <div class="flex justify-center space-x-4 mt-4">
            <a href="#" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition-colors duration-300">
                <i class="fab fa-facebook-f"></i>
            </a>
            <a href="#" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition-colors duration-300">
                <i class="fab fa-twitter"></i>
            </a>
            <a href="#" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition-colors duration-300">
                <i class="fab fa-instagram"></i>
            </a>
        </div>
    </div>
</footer>
<script>
    // 展开/收起功能
    function toggleExpand(cityId) {
        const button = document.querySelector(`.${cityId === 'main-world' ? 'main-world-city' : 'city-description'} .expand-button`);
        const buttonText = button.querySelector('.button-text');
        const content = document.getElementById(`${cityId}-expandedContent`);

        button.classList.toggle('active');
        content.classList.toggle('active');

        if (button.classList.contains('active')) {
            buttonText.textContent = document.querySelector(`.${cityId === 'main-world' ? 'main-world-city' : 'city-description'} .expand-button .button-text[data-lang="${document.documentElement.lang}"]`).textContent === '详情'? '收起' : 'Hide';
        } else {
            buttonText.textContent = document.querySelector(`.${cityId === 'main-world' ? 'main-world-city' : 'city-description'} .expand-button .button-text[data-lang="${document.documentElement.lang}"]`).textContent === '详情'? '详情' : 'Details';
        }

        if (content.classList.contains('active')) {
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

    // 语言切换功能
    function changeLanguage(lang) {
        document.documentElement.lang = lang;
        const allLangElements = document.querySelectorAll('[data-lang]');
        allLangElements.forEach(element => {
            if (element.getAttribute('data-lang') === lang) {
                element.style.display = 'block';
            } else {
                element.style.display = 'none';
            }
        });
        // 隐藏语言选项框
        const languageOptions = document.getElementById('languageOptions');
        languageOptions.classList.remove('show');
    }

    // 显示语言选项框
    function toggleLanguageOptions() {
        const languageOptions = document.getElementById('languageOptions');
        languageOptions.classList.toggle('show');
    }
    </script>
</body>
</html>
    
