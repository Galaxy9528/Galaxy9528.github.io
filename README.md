<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>虚空堡垒丨原版生存服务器 - Minecraft 1.21.4</title>
    <style>
        :root {
            --mc-green: #3b5b4f;
            --mc-orange: #f2a33a;
            --mc-dark: #2d2d2d;
        }

        body {
            font-family: 'Microsoft YaHei', Arial, sans-serif;
            line-height: 1.8;
            margin: 0;
            padding: 20px;
            background: #f0f0f0 url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAQAAAAECAYAAACp8Z5+AAAAIklEQVQIW2NkQAKrVq36zwjjgzhhYWGMYAEYB8RmROaABADeOQ8CXl/xfgAAAABJRU5ErkJggg==');
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255,255,255,0.95);
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 8px 30px rgba(0,0,0,0.1);
            backdrop-filter: blur(5px);
        }

        h1, h2 {
            color: var(--mc-green);
            border-bottom: 3px solid var(--mc-orange);
            padding-bottom: 12px;
            margin: 30px 0 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            border-radius: 10px;
        }

        .version-badge {
            background: var(--mc-orange);
            color: white;
            padding: 8px 25px;
            border-radius: 25px;
            display: inline-block;
            margin: 15px 0;
            font-size: 1.1em;
            box-shadow: 0 3px 6px rgba(242,163,58,0.2);
        }

        .feature-list {
            display: grid;
            grid-gap: 25px;
            margin: 25px 0;
        }

        .feature-card {
            padding: 25px;
            border-left: 5px solid var(--mc-green);
            background: #f8f9fa;
            border-radius: 5px;
            transition: transform 0.3s;
        }

        .feature-card:hover {
            transform: translateX(10px);
        }

        .main-city {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin: 40px 0;
            align-items: center;
        }

        .city-description {
            padding: 25px;
            background: #fff8f0;
            border-radius: 10px;
            position: relative;
        }

        .city-description::before {
            content: "🏰";
            font-size: 3em;
            position: absolute;
            right: 20px;
            top: -30px;
            opacity: 0.2;
        }

        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .gallery img {
            width: 100%;
            height: 220px;
            object-fit: cover;
            border-radius: 8px;
            border: 2px solid var(--mc-green);
            transition: all 0.3s;
        }

        .gallery img:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        }

        .join-button {
            display: inline-flex;
            align-items: center;
            background: var(--mc-green);
            color: white!important;
            padding: 15px 40px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            margin: 25px 0;
            transition: all 0.3s;
        }

        .join-button:hover {
            background: #2d4a42;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(59,91,79,0.3);
        }

        @media (max-width: 768px) {
            .main-city {
                grid-template-columns: 1fr;
            }
            .gallery {
                grid-template-columns: 1fr 1fr;
            }
            .feature-card {
                padding: 20px;
            }
        }

        @media (max-width: 480px) {
            .gallery {
                grid-template-columns: 1fr;
            }
            .version-badge {
                font-size: 1em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>虚空堡垒生存服务器</h1>
            <div class="version-badge">Java版 1.21.4 | 长期更新</div>
            <p>兼容版本：1.20.x - 1.21.4 | 类型：原版生存丨自由建造</p>
        </div>

        <h2>🌟 核心特色</h2>
        <div class="feature-list">
            <div class="feature-card">
                <h3>纯净原版体验</h3>
                <p>• 零插件/零魔改，完整保留MC原版机制<br>
                • 支持1.20-1.21.4全版本互通，即时体验试炼密室等新内容</p>
            </div>
            <div class="feature-card">
                <h3>永久发展世界</h3>
                <p>• 自2020年持续运营，地图永不重置<br>
                • 三界全开放，完整保留每位玩家的建造足迹</p>
            </div>
            <div class="feature-card">
                <h3>高性能保障</h3>
                <p>• 专业游戏服务器配置，TPS稳定20<br>
                • 智能防熊系统 + 每日自动备份</p>
            </div>
        </div>

        <h2>🏰 末地主城揭秘</h2>
        <div class="main-city">
            <img src="https://avenues-my.sharepoint.cn/:i:/g/personal/nature_gao_2030_students_avenueschina_cn/EZX7pS9W9XhCuUuyqJeeK48BDjQldVmNTXeRTO0qIMikFw?e=miLHjp" 
                 alt="末地主城全景" 
                 style="border-radius: 15px;box-shadow: 0 10px 30px rgba(0,0,0,0.2);">
            <div class="city-description">
                <h3>虚空中的机械奇观</h3>
                <p>悬浮于末地虚空的巨型堡垒，以精密几何结构构建的赛博朋克风格主城。中心能量核心辐射出炽热的橙红光芒，延伸出机械臂般的分支结构。黑曜石基底与石英装饰形成强烈对比，流动的熔岩线路贯穿整个建筑群。</p>
                <p>内部包含：<br>
                • 四向立体交通网络<br>
                • 全自动红石导航系统<br>
                • 玩家交易大厅<br>
                • 隐藏密室挑战区</p>
            </div>
        </div>

        <h2>⚖️ 服务器守则</h2>
        <div style="background:#f8d7da;padding:20px;border-radius:10px;">
            <ul>
                <li>🛑 严禁任何作弊行为（包括但不限于X-Ray、自动钓鱼）</li>
                <li>🔒 私人领地不可破坏/偷窃（违者回档处理）</li>
                <li>💬 文明交流，禁止广告/引战/刷屏</li>
            </ul>
        </div>

        <h2>🚪 加入指南</h2>
        <div style="margin:25px 0;">
            <p>加入流程：</p>
            <ol>
                <li>添加DY官方群获取审核表</li>
                <li>完整填写入服问卷（含MC经历调查）</li>
                <li>48小时内邮件发送IP及白名单</li>
            </ol>
            <a href="https://www.wjx.cn/vm/OAfb7GX.aspx#" 
               class="join-button"
               target="_blank">
               📝 立即申请加入
            </a>
        </div>

        <h2>🔧 版本说明</h2>
        <div style="background:#e2f4fc;padding:20px;border-radius:10px;">
            <p>推荐设置：</p>
            <ul>
                <li>必须使用正版启动器</li>
                <li>首选1.21.4版本获得完整体验</li>
                <li>1.20.x版本可连接但部分新方块不可交互</li>
                <li>出现连接问题请检查JAVA版本</li>
            </ul>
        </div>
    </div>
</body>
</html>
