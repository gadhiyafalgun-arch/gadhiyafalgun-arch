<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #000;
            color: #fff;
            font-family: 'Courier New', monospace;
            overflow-x: hidden;
        }

        /* Matrix Canvas Background */
        #matrixCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: #000;
        }

        /* Content Container */
        .content-wrapper {
            position: relative;
            z-index: 10;
            background: rgba(0, 0, 0, 0.60);
            backdrop-filter: blur(2px);
        }

        /* Header Section */
        .header {
            text-align: center;
            padding: 40px 20px;
            border-bottom: 2px solid #00d4ff;
            animation: fadeIn 2s ease-in;
        }

        .greeting {
            font-size: 28px;
            color: #ff006e;
            margin-bottom: 20px;
            text-shadow: 0 0 10px #ff006e, 0 0 20px #ff006e;
            animation: glow 2s infinite alternate;
        }

        .typing-text {
            font-size: 22px;
            color: #00d4ff;
            text-shadow: 0 0 10px #00d4ff, 0 0 20px #00d4ff;
            margin-bottom: 20px;
            animation: typing 3s steps(40, end);
        }

        /* Navigation */
        nav {
            text-align: center;
            padding: 20px;
            border-bottom: 1px solid #00d4ff33;
        }

        nav a {
            color: #00d4ff;
            text-decoration: none;
            margin: 0 15px;
            padding: 10px 20px;
            border: 1px solid #00d4ff33;
            border-radius: 5px;
            transition: all 0.3s ease;
            display: inline-block;
            text-shadow: 0 0 5px #00d4ff;
        }

        nav a:hover {
            color: #000;
            background: #00d4ff;
            text-shadow: none;
            box-shadow: 0 0 20px #00d4ff;
        }

        /* Section */
        .section {
            padding: 40px 20px;
            margin: 20px;
            border: 2px solid #ff006e44;
            border-radius: 10px;
            background: rgba(0, 0, 0, 0.4);
            animation: slideIn 0.8s ease-out;
        }

        .section h2 {
            color: #ff006e;
            margin-bottom: 20px;
            text-shadow: 0 0 10px #ff006e, 0 0 20px #ff006e;
            border-bottom: 2px solid #00d4ff;
            padding-bottom: 10px;
            font-size: 28px;
        }

        .section h3 {
            color: #00d4ff;
            margin: 15px 0 10px 0;
            text-shadow: 0 0 5px #00d4ff;
        }

        .section p {
            line-height: 1.8;
            color: #ccc;
            margin-bottom: 15px;
        }

        /* Tech Stack Badges */
        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin: 20px 0;
        }

        .badge {
            background: rgba(0, 212, 255, 0.1);
            border: 1px solid #00d4ff;
            color: #00d4ff;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 12px;
            transition: all 0.3s ease;
            text-shadow: 0 0 5px #00d4ff;
        }

        .badge:hover {
            background: #00d4ff;
            color: #000;
            box-shadow: 0 0 15px #00d4ff;
            transform: scale(1.1);
        }

        /* Skills Table */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }

        .skill-box {
            background: rgba(255, 0, 110, 0.05);
            border: 1px solid #ff006e44;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .skill-box:hover {
            background: rgba(255, 0, 110, 0.15);
            border-color: #ff006e;
            box-shadow: 0 0 20px #ff006e44;
            transform: translateY(-5px);
        }

        .skill-box h4 {
            color: #00d4ff;
            margin-bottom: 10px;
            text-shadow: 0 0 5px #00d4ff;
        }

        .skill-icon {
            font-size: 40px;
            margin-bottom: 10px;
        }

        /* Social Links */
        .socials {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .social-btn {
            width: 50px;
            height: 50px;
            border: 2px solid #00d4ff;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #00d4ff;
            text-decoration: none;
            font-size: 24px;
            transition: all 0.3s ease;
            background: rgba(0, 212, 255, 0.05);
            text-shadow: 0 0 5px #00d4ff;
        }

        .social-btn:hover {
            background: #00d4ff;
            color: #000;
            box-shadow: 0 0 20px #00d4ff;
            transform: scale(1.2) rotate(10deg);
        }

        /* Stats Section */
        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }

        .stat-card {
            background: rgba(0, 212, 255, 0.08);
            border: 1px solid #00d4ff;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .stat-card:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px #00d4ff44;
        }

        .stat-number {
            font-size: 28px;
            color: #ff006e;
            font-weight: bold;
            text-shadow: 0 0 10px #ff006e;
        }

        .stat-label {
            color: #00d4ff;
            font-size: 12px;
            margin-top: 5px;
            text-shadow: 0 0 5px #00d4ff;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 40px 20px;
            border-top: 2px solid #00d4ff;
            margin-top: 40px;
            color: #00d4ff;
            text-shadow: 0 0 5px #00d4ff;
        }

        footer a {
            color: #ff006e;
            text-decoration: none;
            transition: all 0.3s ease;
            text-shadow: 0 0 5px #ff006e;
        }

        footer a:hover {
            text-shadow: 0 0 10px #ff006e;
        }

        /* Animations */
        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes glow {
            from {
                text-shadow: 0 0 10px #00ff00;
            }
            to {
                text-shadow: 0 0 20px #00ff00, 0 0 30px #00ff00;
            }
        }

        @keyframes typing {
            from {
                width: 0;
            }
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-20px);
            }
        }

        /* Container */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .tech-stack {
                justify-content: flex-start;
            }

            .section {
                margin: 15px 0;
                padding: 20px 15px;
            }

            .skills-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Matrix Canvas -->
    <canvas id="matrixCanvas"></canvas>

    <!-- Content -->
    <div class="content-wrapper">
        <!-- Header -->
        <div class="header">
            <div class="greeting">💻 Hello, World! 👋</div>
            <div class="typing-text">Welcome to My Profile | ML Enthusiast | Full Stack Developer</div>
        </div>

        <!-- Navigation -->
        <nav>
            <a href="#about">About</a>
            <a href="#skills">Skills</a>
            <a href="#projects">Projects</a>
            <a href="#contact">Contact</a>
        </nav>

        <!-- Main Container -->
        <div class="container">
            <!-- About Section -->
            <div class="section" id="about">
                <h2>👤 About Me</h2>
                <p>I'm a passionate developer from India, continuously learning and improving myself. I love building meaningful projects that contribute to technological advancement.</p>
                <p><strong>Current Focus:</strong></p>
                <ul style="margin-left: 20px; color: #ccc;">
                    <li>📚 Machine Learning & AI</li>
                    <li>🌐 Web Development</li>
                    <li>📊 Data Science & Analytics</li>
                    <li>💡 Creative Problem Solving</li>
                </ul>
                <p style="margin-top: 20px;"><strong>Contact:</strong> <span style="color: #00ff00;">gadhiyafalgun.02@gmail.com</span></p>
                <p style="margin-top: 10px;"><strong>Portfolio:</strong> <a href="#" style="color: #00ff00;">Check My Work</a></p>
            </div>

            <!-- Social Links -->
            <div class="section">
                <h2>🌐 Connect With Me</h2>
                <div class="socials">
                    <a href="https://linkedin.com/in/falgun-gadhiya-47a563346" class="social-btn" title="LinkedIn">in</a>
                    <a href="https://github.com/gadhiyafalgun-arch" class="social-btn" title="GitHub">⚙</a>
                    <a href="mailto:gadhiyafalgun.02@gmail.com" class="social-btn" title="Email">✉</a>
                    <a href="https://twitter.com" class="social-btn" title="Twitter">𝕏</a>
                    <a href="https://hackerrank.com" class="social-btn" title="HackerRank">H</a>
                </div>
            </div>

            <!-- Tech Stack Section -->
            <div class="section" id="skills">
                <h2>💻 Tech Stack</h2>
                <div class="tech-stack">
                    <span class="badge">Python</span>
                    <span class="badge">JavaScript</span>
                    <span class="badge">HTML5</span>
                    <span class="badge">CSS3</span>
                    <span class="badge">React</span>
                    <span class="badge">Node.js</span>
                    <span class="badge">MongoDB</span>
                    <span class="badge">MySQL</span>
                    <span class="badge">TensorFlow</span>
                    <span class="badge">PyTorch</span>
                    <span class="badge">NumPy</span>
                    <span class="badge">Pandas</span>
                    <span class="badge">Git</span>
                    <span class="badge">AWS</span>
                </div>
            </div>

            <!-- Skills Section -->
            <div class="section" id="skills-detail">
                <h2>🛠 Skills Breakdown</h2>
                <div class="skills-grid">
                    <div class="skill-box">
                        <div class="skill-icon">🎨</div>
                        <h4>Frontend</h4>
                        <p>React, HTML5, CSS3, Tailwind, JavaScript</p>
                    </div>
                    <div class="skill-box">
                        <div class="skill-icon">⚙</div>
                        <h4>Backend</h4>
                        <p>Node.js, Python, MongoDB, MySQL</p>
                    </div>
                    <div class="skill-box">
                        <div class="skill-icon">🤖</div>
                        <h4>Machine Learning</h4>
                        <p>TensorFlow, PyTorch, scikit-learn</p>
                    </div>
                    <div class="skill-box">
                        <div class="skill-icon">📊</div>
                        <h4>Data Science</h4>
                        <p>NumPy, Pandas, Matplotlib, Plotly</p>
                    </div>
                    <div class="skill-box">
                        <div class="skill-icon">🔧</div>
                        <h4>Tools</h4>
                        <p>Git, AWS, Google Cloud, Postman</p>
                    </div>
                    <div class="skill-box">
                        <div class="skill-icon">🎯</div>
                        <h4>Soft Skills</h4>
                        <p>Problem Solving, Communication, Leadership</p>
                    </div>
                </div>
            </div>

            <!-- Stats Section -->
            <div class="section">
                <h2>📈 Stats</h2>
                <div class="stats">
                    <div class="stat-card">
                        <div class="stat-number">50+</div>
                        <div class="stat-label">Projects</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">1000+</div>
                        <div class="stat-label">Commits</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">5</div>
                        <div class="stat-label">Years of Experience</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">100%</div>
                        <div class="stat-label">Passion</div>
                    </div>
                </div>
            </div>

            <!-- Projects Section -->
            <div class="section" id="projects">
                <h2>🚀 Featured Projects</h2>
                <div class="skills-grid">
                    <div class="skill-box">
                        <h4>Hand Tracking AR-UI</h4>
                        <p>Python-based augmented reality project with hand tracking capabilities.</p>
                    </div>
                    <div class="skill-box">
                        <h4>AI Face Emotion Overlay</h4>
                        <p>Real-time emotion detection with cyberpunk HUD visualization.</p>
                    </div>
                    <div class="skill-box">
                        <h4>Nokia Snake Game</h4>
                        <p>Classic game with gesture control using Python and OpenCV.</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <footer>
            <p>© 2024 Your Name. All rights reserved.</p>
            <p style="margin-top: 10px; color: #0f0;">Keep Building. Keep Growing. 🚀</p>
        </footer>
    </div>

    <script>
        // Matrix Canvas Animation
        const canvas = document.getElementById('matrixCanvas');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const characters = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
        const charArray = characters.split('');

        const fontSize = 16;
        const columns = Math.floor(canvas.width / fontSize);
        const drops = [];

        for (let i = 0; i < columns; i++) {
            drops[i] = Math.floor(Math.random() * canvas.height / fontSize);
        }

        function drawMatrix() {
            // Semi-transparent black background for trail effect
            ctx.fillStyle = 'rgba(0, 0, 0, 0.08)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            ctx.font = fontSize + 'px "Courier New"';
            ctx.shadowBlur = 15;

            // Array of sci-fi tech colors
            const colors = ['#00d4ff', '#ff006e', '#00ff41', '#9d4edd', '#ff006e', '#00f5ff', '#00d4ff'];
            const charArray = characters.split('');

            for (let i = 0; i < drops.length; i++) {
                const char = charArray[Math.floor(Math.random() * charArray.length)];
                const x = i * fontSize;
                const y = drops[i] * fontSize;

                // Super slow color change - change color every 120 frames instead of every frame
                const colorIndex = Math.floor((drops[i] + i) / 6) % colors.length;
                const color = colors[colorIndex];
                ctx.fillStyle = color;
                ctx.shadowColor = color;
                ctx.fillText(char, x, y);

                // Increase drops slower (decreased speed)
                if (Math.random() > 0.975) {
                    drops[i]++;
                }

                // Reset drops to top
                if (drops[i] * fontSize > canvas.height) {
                    drops[i] = 0;
                }
            }
        }

        function animate() {
            drawMatrix();
            requestAnimationFrame(animate);
        }

        animate();

        // Handle window resize
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });

        // Scroll reveal animations
        const sections = document.querySelectorAll('.section');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'slideIn 0.8s ease-out';
                }
            });
        });

        sections.forEach(section => {
            observer.observe(section);
        });
    </script>
</body>
</html>
