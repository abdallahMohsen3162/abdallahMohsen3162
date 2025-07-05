<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Languages & Tools - Enhanced</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 40px 20px;
            position: relative;
            overflow-x: hidden;
        }
        /* Animated background particles */
        
        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
        }
        
        @keyframes float {
            0%,
            100% {
                transform: translateY(0px) rotate(0deg);
            }
            50% {
                transform: translateY(-20px) rotate(180deg);
            }
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }
        
        .section-header {
            text-align: center;
            margin-bottom: 60px;
            position: relative;
        }
        
        .section-title {
            font-size: 3.5rem;
            font-weight: 700;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
            background-size: 400% 400%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 4s ease-in-out infinite;
            margin-bottom: 20px;
            text-shadow: 0 0 30px rgba(255, 255, 255, 0.1);
        }
        
        @keyframes gradientShift {
            0%,
            100% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
        }
        
        .section-subtitle {
            font-size: 1.2rem;
            color: rgba(255, 255, 255, 0.8);
            font-weight: 300;
            letter-spacing: 1px;
        }
        
        .tools-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
            gap: 30px;
            padding: 20px;
        }
        
        .tool-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 25px;
            text-align: center;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 1px solid rgba(255, 255, 255, 0.2);
            position: relative;
            overflow: hidden;
            cursor: pointer;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }
        
        .tool-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transform: rotate(45deg);
            transition: all 0.6s;
            opacity: 0;
        }
        
        .tool-card:hover::before {
            animation: shimmer 1.5s ease-in-out;
            opacity: 1;
        }
        
        @keyframes shimmer {
            0% {
                transform: translateX(-100%) translateY(-100%) rotate(45deg);
            }
            100% {
                transform: translateX(100%) translateY(100%) rotate(45deg);
            }
        }
        
        .tool-card:hover {
            transform: translateY(-10px) scale(1.05);
            background: rgba(255, 255, 255, 0.2);
            border-color: rgba(255, 255, 255, 0.4);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.2);
        }
        
        .tool-icon {
            width: 60px;
            height: 60px;
            object-fit: contain;
            margin-bottom: 15px;
            transition: all 0.3s ease;
            filter: brightness(0.9);
        }
        
        .tool-card:hover .tool-icon {
            transform: scale(1.1) rotate(5deg);
            filter: brightness(1.1) drop-shadow(0 4px 8px rgba(0, 0, 0, 0.2));
        }
        
        .tool-name {
            font-size: 0.9rem;
            font-weight: 600;
            color: rgba(255, 255, 255, 0.9);
            margin-top: 10px;
            opacity: 0;
            transform: translateY(10px);
            transition: all 0.3s ease;
        }
        
        .tool-card:hover .tool-name {
            opacity: 1;
            transform: translateY(0);
        }
        /* Pulse animation for standout technologies */
        
        .featured {
            animation: pulse 3s ease-in-out infinite;
        }
        
        @keyframes pulse {
            0%,
            100% {
                box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1), 0 0 0 0 rgba(255, 255, 255, 0.3);
            }
            50% {
                box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1), 0 0 0 10px rgba(255, 255, 255, 0.1);
            }
        }
        /* Responsive design */
        
        @media (max-width: 768px) {
            .section-title {
                font-size: 2.5rem;
            }
            .tools-grid {
                grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
                gap: 20px;
            }
            .tool-card {
                padding: 20px;
            }
        }
        
        @media (max-width: 480px) {
            .section-title {
                font-size: 2rem;
            }
            .tools-grid {
                grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
                gap: 15px;
            }
        }
        /* Loading animation */
        
        .tool-card {
            animation: slideInUp 0.6s ease-out forwards;
            opacity: 0;
            transform: translateY(50px);
        }
        
        @keyframes slideInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        /* Staggered animation delays */
        
        .tool-card:nth-child(1) {
            animation-delay: 0.1s;
        }
        
        .tool-card:nth-child(2) {
            animation-delay: 0.2s;
        }
        
        .tool-card:nth-child(3) {
            animation-delay: 0.3s;
        }
        
        .tool-card:nth-child(4) {
            animation-delay: 0.4s;
        }
        
        .tool-card:nth-child(5) {
            animation-delay: 0.5s;
        }
        
        .tool-card:nth-child(6) {
            animation-delay: 0.6s;
        }
        
        .tool-card:nth-child(7) {
            animation-delay: 0.7s;
        }
        
        .tool-card:nth-child(8) {
            animation-delay: 0.8s;
        }
        
        .tool-card:nth-child(9) {
            animation-delay: 0.9s;
        }
        
        .tool-card:nth-child(10) {
            animation-delay: 1.0s;
        }
        
        .tool-card:nth-child(11) {
            animation-delay: 1.1s;
        }
        
        .tool-card:nth-child(12) {
            animation-delay: 1.2s;
        }
        
        .tool-card:nth-child(13) {
            animation-delay: 1.3s;
        }
        
        .tool-card:nth-child(14) {
            animation-delay: 1.4s;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="section-header">
            <h1 class="section-title">Languages & Tools</h1>
            <p class="section-subtitle">Technologies that power modern development</p>
        </div>

        <div class="tools-grid">
            <div class="tool-card featured">
                <a href="https://getbootstrap.com" target="_blank" rel="noreferrer">
                    <img src="https://getbootstrap.com/docs/5.3/assets/brand/bootstrap-logo-shadow@2x.png" alt="bootstrap" class="tool-icon" />
                    <div class="tool-name">Bootstrap</div>
                </a>
            </div>

            <div class="tool-card">
                <a href="https://canvasjs.com" target="_blank" rel="noreferrer">
                    <img src="https://canvasjs.com/wp-content/uploads/images/logo/canvasjs-logo-240x100.webp" alt="canvasjs" class="tool-icon" />
                    <div class="tool-name">CanvasJS</div>
                </a>
            </div>

            <div class="tool-card featured">
                <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" class="tool-icon" />
                    <div class="tool-name">JavaScript</div>
                </a>
            </div>

            <div class="tool-card">
                <a href="https://www.microsoft.com/en-us/sql-server" target="_blank" rel="noreferrer">
                    <img src="https://www.svgrepo.com/show/303229/microsoft-sql-server-logo.svg" alt="mssql" class="tool-icon" />
                    <div class="tool-name">MS SQL Server</div>
                </a>
            </div>

            <div class="tool-card">
                <a href="https://www.mysql.com/" target="_blank" rel="noreferrer">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" class="tool-icon" />
                    <div class="tool-name">MySQL</div>
                </a>
            </div>

            <div class="tool-card featured">
                <a href="https://nextjs.org/" target="_blank" rel="noreferrer">
                    <img src="https://cdn.worldvectorlogo.com/logos/nextjs-2.svg" alt="nextjs" class="tool-icon" />
                    <div class="tool-name">Next.js</div>
                </a>
            </div>

            <div class="tool-card">
                <a href="https://www.postgresql.org" target="_blank" rel="noreferrer">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" class="tool-icon" />
                    <div class="tool-name">PostgreSQL</div>
                </a>
            </div>

            <div class="tool-card featured">
                <a href="https://www.python.org" target="_blank" rel="noreferrer">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" class="tool-icon" />
                    <div class="tool-name">Python</div>
                </a>
            </div>

            <div class="tool-card featured">
                <a href="https://reactjs.org/" target="_blank" rel="noreferrer">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="react" class="tool-icon" />
                    <div class="tool-name">React</div>
                </a>
            </div>

            <div class="tool-card">
                <a href="https://redux.js.org" target="_blank" rel="noreferrer">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/redux/redux-original.svg" alt="redux" class="tool-icon" />
                    <div class="tool-name">Redux</div>
                </a>
            </div>

            <div class="tool-card featured">
                <a href="https://www.typescriptlang.org/" target="_blank" rel="noreferrer">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" alt="typescript" class="tool-icon" />
                    <div class="tool-name">TypeScript</div>
                </a>
            </div>

            <div class="tool-card">
                <a href="https://vuejs.org/" target="_blank" rel="noreferrer">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/vuejs/vuejs-original-wordmark.svg" alt="vuejs" class="tool-icon" />
                    <div class="tool-name">Vue.js</div>
                </a>
            </div>

            <div class="tool-card">
                <a href="https://nestjs.com/" target="_blank" rel="noreferrer">
                    <img src="https://nestjs.com/img/logo-small.svg" alt="nestjs" class="tool-icon" />
                    <div class="tool-name">NestJS</div>
                </a>
            </div>

            <div class="tool-card">
                <a href="https://ant.design/" target="_blank" rel="noreferrer">
                    <img src="https://gw.alipayobjects.com/zos/rmsportal/KDpgvguMpGfqaHPjicRK.svg" alt="ant-design" class="tool-icon" />
                    <div class="tool-name">Ant Design</div>
                </a>
            </div>
        </div>
    </div>

    <script>
        // Create animated background particles
        function createParticles() {
            const particleCount = 15;
            const body = document.body;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 6 + 's';
                particle.style.animationDuration = (Math.random() * 3 + 4) + 's';
                body.appendChild(particle);
            }
        }

        // Enhanced card interactions
        document.querySelectorAll('.tool-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-15px) scale(1.08) rotate(2deg)';
            });

            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1) rotate(0deg)';
            });
        });

        // Initialize particles when page loads
        window.addEventListener('load', createParticles);

        console.log("🚀 Enhanced Languages and Tools section loaded successfully with premium styling!");
    </script>
</body>

</html>
