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
            --grid-color: rgba(255,107,53,0.05);
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
            overflow: hidden;
        }

        .header-section::before {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,107,53,0.1) 0%, transparent 70%);
            animation: pulse 8s linear infinite;
            z-index: -1;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: rgba(30, 30, 30, 0.97);
            padding: 0;
            border-radius: 10px;
            overflow: hidden;
        }

        h1 {
            color: var(--mc-orange);
            border-left: 5px solid var(--mc-green);
            padding-left: 15px;
            margin: 0 0 20px;
            position: relative;
            z-index: 1;
        }

        .version-box {
            background: rgba(255,107,53,0.1);
            padding: 20px;
            border-radius: 8px;
            position: relative;
            z-index: 1;
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
        }

        @keyframes pulse {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
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
        </div>

        <div class="city-description">
            <h2>末地主城</h2>
            <p>服务器的末地主城外观极具科幻感与未来感。整体建筑以黑白为主色调，搭配亮眼的橙色装饰，形成强烈视觉冲击。</p>
            <p>主城结构错综复杂，由大量几何形状模块拼接而成。从空中俯瞰，中心是巨大的圆形构造，如能量核心般散发着橙色光芒，向外辐射出多条类似机械臂的建筑分支，布满精密的结构和装置，仿佛随时会启动运转。</p>
            <p>建筑外部，巨大的框架和延伸的平台相互交错，部分区域悬空，给人以悬浮之感。走进其中，通道和房间相连，天花板和墙壁上分布着发光条纹和方块，照亮内部空间。有的区域像是大型工厂，林立着高耸的机械柱和管道；有的则类似指挥中心，有着开阔的视野和复杂的操控台外观。</p>
            <p>主城背景是浩瀚星空，远处的行星在光影渲染下更显神秘，与末地主城的科技风外观相映衬，仿佛是宇宙中的一座神秘堡垒。</p>
        </div>
    </div>
</body>
</html>
