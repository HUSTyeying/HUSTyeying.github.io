（无主题）
HUST夜莺<2930054576@qq.com>
我<2930054576@qq.com>

<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- 适配移动端 -->
    <title>鲍清衔的个人页面</title>
    <!-- 引入图标库（增强技能视觉表达） -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css">
    <style>
        /* 基础重置与全局样式 */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            overflow: hidden; 
            position: relative; 
            min-height: 100vh;
            font-family: 'Arial', 'Roboto', sans-serif;
            /* 页面加载淡入（静态过渡效果） */
            opacity: 0;
            animation: pageFadeIn 1.5s ease forwards;
        }

        /* 1. 科幻动态背景 */
        #sciFiBg { 
            position: absolute; top: 0; left: 0; 
            width: 100vw; height: 100vh; 
            z-index: -1; 
            background: linear-gradient(135deg, #000010 0%, #0a192f 100%); /* 渐变底色，更有层次 */
        }

        /* 2. 个人介绍主卡片（核心容器） */
        .intro-card {
            position: absolute; 
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            padding: 3rem 4rem;
            width: 90%; max-width: 600px; /* 响应式宽度，避免大屏过宽 */
            background: rgba(10, 15, 35, 0.7); 
            backdrop-filter: blur(8px); /* 毛玻璃效果（静态高级感） */
            border: 1px solid;
            /* 霓虹渐变边框（静态视觉亮点） */
            border-image: linear-gradient(45deg, #4CC9F0, #BFDBFE, #A7F3D0) 1;
            border-radius: 16px;
            box-shadow: 
                0 0 25px rgba(76, 201, 240, 0.2), 
                0 0 50px rgba(191, 219, 254, 0.15),
                inset 0 0 10px rgba(156, 211, 156, 0.1); /* 内发光，增强立体感 */
            z-index: 1;
            /* 卡片入场动画（动态效果） */
            transform: translate(-50%, -50%) scale(0.9);
            animation: cardPopIn 1.2s ease 0.3s forwards;
        }

        /* 3. 基本信息样式 */
        .intro-header { margin-bottom: 2.5rem; text-align: center; }
        .intro-name {
            font-size: 2.5rem;
            color: #4CC9F0;
            margin-bottom: 0.8rem;
            letter-spacing: 0.08em;
            /* 姓名霓虹闪烁（弱动态） */
            text-shadow: 0 0 8px rgba(76, 201, 240, 0.4), 0 0 20px rgba(76, 201, 240, 0.2);
            animation: namePulse 3s ease infinite alternate;
        }
        .intro-school {
            font-size: 1.2rem;
            color: #BFDBFE;
            line-height: 1.8;
        }

        /* 4. 技能模块样式 */
        .skills-title {
            font-size: 1.4rem;
            color: #A7F3D0;
            text-align: center;
            margin-bottom: 1.8rem;
            padding-bottom: 0.8rem;
            border-bottom: 1px dashed rgba(167, 243, 208, 0.3); /* 虚线分隔，静态细节 */
        }
        .skills-list {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap; /* 移动端自动换行 */
            gap: 2rem;
        }
        .skill-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 120px;
            cursor: pointer;
            /* 技能项初始状态（为hover动画做准备） */
            transition: all 0.5s ease;
            opacity: 0.8;
            transform: translateY(10px);
            /* 技能项依次入场（动态效果） */
            animation: skillFadeUp 0.8s ease forwards;
        }
        /* 技能项延迟入场，增强层次感 */
        .skill-item:nth-child(1) { animation-delay: 0.6s; }
        .skill-item:nth-child(2) { animation-delay: 0.9s; }

        /* 技能项hover交互（核心动态效果） */
        .skill-item:hover {
            opacity: 1;
            transform: translateY(-5px) scale(1.1); /* 上浮+放大 */
        }
        .skill-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            /* 图标颜色区分技能类型 */
            color: #4CC9F0;
            /* 图标发光效果 */
            text-shadow: 0 0 10px rgba(76, 201, 240, 0.5);
            transition: all 0.5s ease;
        }
        .skill-item:nth-child(2) .skill-icon { color: #A7F3D0; text-shadow: 0 0 10px rgba(167, 243, 208, 0.5); }
        .skill-item:hover .skill-icon {
            transform: rotate(5deg) scale(1.2); /* 轻微旋转+放大 */
            text-shadow: 0 0 15px rgba(76, 201, 240, 0.7);
        }
        .skill-item:nth-child(2):hover .skill-icon { text-shadow: 0 0 15px rgba(167, 243, 208, 0.7); }
        .skill-name {
            font-size: 1.1rem;
            color: #E0E7FF;
            transition: color 0.5s ease;
        }
        .skill-item:hover .skill-name { color: #4CC9F0; }
        .skill-item:nth-child(2):hover .skill-name { color: #A7F3D0; }

        /* 5. 所有动画关键帧定义 */
        /* 页面加载淡入 */
        @keyframes pageFadeIn {
            to { opacity: 1; }
        }
        /* 卡片弹出入场 */
        @keyframes cardPopIn {
            to { transform: translate(-50%, -50%) scale(1); }
        }
        /* 姓名霓虹脉冲 */
        @keyframes namePulse {
            to { text-shadow: 0 0 12px rgba(76, 201, 240, 0.6), 0 0 30px rgba(76, 201, 240, 0.4); }
        }
        /* 技能项向上淡入 */
        @keyframes skillFadeUp {
            to { opacity: 0.8; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <!-- 1. 科幻动态背景Canvas -->
    <canvas id="sciFiBg"></canvas>

    <!-- 2. 个人介绍主卡片（含技能模块） -->
    <div class="intro-card">
        <!-- 基本信息 -->
        <div class="intro-header">
            <h1 class="intro-name">鲍清衔</h1>
            <p class="intro-school">就读于华中科技大学</p>
            <p class="intro-school">软件学院学生</p>
        </div>

        <!-- 技能模块（新增） -->
        <h2 class="skills-title">个人技能</h2>
        <div class="skills-list">
            <!-- 写代码技能（配代码图标） -->
            <div class="skill-item">
                <i class="fa fa-code skill-icon" aria-hidden="true"></i>
                <span class="skill-name">写代码</span>
            </div>
            <!-- 组织活动技能（配用户组图标） -->
            <div class="skill-item">
                <i class="fa fa-users skill-icon" aria-hidden="true"></i>
                <span class="skill-name">组织活动</span>
            </div>
        </div>
    </div>

    <!-- 3. 原有SDK代码 -->
    <script src="https://agi-dev-platform-web.cdn.bcebos.com/ai_apaas/embed/output/embedLiteSDK.js?responseExpires=0&t=1763776319977"></script>
    <script>
        new EmbedLiteSDK({appId: 'd5709b98-ba74-4f97-aadb-53911d56f57d', code: 'embedwSDpPRYK4aV8WTroTZpd'});
    </script>

    <!-- 4. 背景动态效果（优化增强） -->
    <script>
        const canvas = document.getElementById('sciFiBg');
        const ctx = canvas.getContext('2d');
        let width, height;

        // 屏幕适配
        function resize() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resize);
        resize();

        // --------------- 优化1：网格线增加“闪烁”效果 ---------------
        class GridLine {
            constructor(isHorizontal) {
                this.isHorizontal = isHorizontal;
                this.y = isHorizontal ? Math.random() * height : 0;
                this.x = isHorizontal ? 0 : Math.random() * width;
                this.speed = 0.8 + Math.random() * 1.5; // 速度放缓，更显沉稳
                this.alpha = 0.1 + Math.random() * 0.3;
                this.pulseRate = 0.002 + Math.random() * 0.003; // 闪烁频率随机
            }
            update() {
                // 网格线移动
                this.isHorizontal ? (this.y += this.speed) : (this.x += this.speed);
                // 网格线闪烁（动态增强）
                this.alpha = Math.sin(Date.now() * this.pulseRate) * 0.15 + 0.2; // 正弦曲线控制透明度
                // 超出屏幕重置
                if (this.isHorizontal && this.y > height) this.y = -20;
                if (!this.isHorizontal && this.x > width) this.x = -20;
            }
            draw() {
                ctx.beginPath();
                ctx.strokeStyle = `rgba(76, 201, 240, ${this.alpha})`;
                ctx.lineWidth = 0.8;
                this.isHorizontal 
                    ? ctx.moveTo(0, this.y).lineTo(width, this.y) 
                    : ctx.moveTo(this.x, 0).lineTo(this.x, height);
                ctx.stroke();
            }
        }

        // --------------- 优化2：粒子增加“尾迹”与“碰撞检测” ---------------
        class Particle {
            constructor() {
                this.reset();
                this.tail = []; // 粒子尾迹（动态新效果）
                this.tailLength = 5; // 尾迹长度
            }
            reset() {
                this.x = Math.random() * width;
                this.y = Math.random() * height;
                this.size = 0.5 + Math.random() * 1.2;
                this.speedX = (Math.random() - 0.5) * 0.6; // 速度降低，避免杂乱
                this.speedY = (Math.random() - 0.5) * 0.6;
                this.color = Math.random() > 0.5 
                    ? `rgba(191, 219, 254, ${0.3 + Math.random() * 0.4})` 
                    : `rgba(156, 211, 156, ${0.3 + Math.random() * 0.4})`;
            }
            update() {
                // 记录尾迹（保存前几帧位置）
                this.tail.unshift({x: this.x, y: this.y});
                if (this.tail.length > this.tailLength) this.tail.pop();

                // 粒子移动
                this.x += this.speedX;
                this.y += this.speedY;

                // 边界反弹（保留原效果）
                if (this.x < 0 || this.x > width) this.speedX *= -1;
                if (this.y < 0 || this.y > height) this.speedY *= -1;

                // 粒子碰撞检测（新动态：靠近时轻微排斥）
                particles.forEach(particle => {
                    if (particle !== this) {
                        const dx = this.x - particle.x;
                        const dy = this.y - particle.y;
                        const dist = Math.sqrt(dx*dx + dy*dy);
                        if (dist < 30) { // 距离小于30时排斥
                            this.x += dx * 0.01;
                            this.y += dy * 0.01;
                            particle.x -= dx * 0.01;
                            particle.y -= dy * 0.01;
                        }
                    }
                });
            }
            draw() {
                // 绘制尾迹（新效果：渐变透明）
                this.tail.forEach((pos, index) => {
                    const alpha = parseFloat(this.color.match(/\d+\.\d+/)[0]) * (1 - index/this.tailLength);
                    const tailColor = this.color.replace(/\d+\.\d+(?=\))/, alpha.toFixed(2));
                    ctx.beginPath();
                    ctx.arc(pos.x, pos.y, this.size * (1 - index/this.tailLength), 0, Math.PI * 2);
                    ctx.fillStyle = tailColor;
                    ctx.fill();
                });
                // 绘制粒子本体
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
            }
        }

        // 初始化元素（数量微调，平衡效果与性能）
        const gridLines = Array.from({length: 60}, () => new GridLine(Math.random() > 0.5));
        const particles = Array.from({length: 150}, () => new Particle());

        // 背景动画循环
        function animate() {
            // 半透明覆盖（保留拖影效果，透明度微调）
            ctx.fillStyle = 'rgba(0, 0, 16, 0.12)';
            ctx.fillRect(0, 0, width, height);

            // 绘制网格与粒子
            gridLines.forEach(line => { line.update(); line.draw(); });
            particles.forEach(particle => { particle.update(); particle.draw(); });

            requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>
   
