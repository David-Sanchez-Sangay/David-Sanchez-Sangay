<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hero Section - David Sánchez</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>

        :root {
            --primary: #3498db;
            --secondary: #2ecc71;
            --accent: #9b59b6;
            --dark: #2c3e50;
            --darker: #1a252f;
            --light: #ecf0f1;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        body {
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, var(--dark), var(--darker));
            color: var(--light);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            text-align: left;
            padding: 2rem;
            box-sizing: border-box;
            overflow-x: hidden;
        }

        .hero-container {
            max-width: 900px;
            width: 100%;
            padding: 4rem;
            background: rgba(26, 37, 47, 0.7);
            border-radius: 15px;
            box-shadow: var(--shadow);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            position: relative;
            overflow: hidden;
            transform-style: preserve-3d;
            perspective: 1000px;
            animation: pulse 8s ease-in-out infinite;
        }

        .hero-container::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(52, 152, 219, 0.1) 0%, transparent 70%);
            animation: rotate 20s linear infinite;
            z-index: -1;
        }

        .hero-container::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(
                45deg,
                transparent 65%,
                rgba(46, 204, 113, 0.1) 100%
            );
            z-index: -1;
            animation: gradientShift 8s ease infinite alternate;
        }

        .hero-text {
            position: relative;
            z-index: 2;
        }

        .hero-text h1 {
            font-size: 3.5rem;
            margin-bottom: 0.75rem;
            background: linear-gradient(45deg, var(--primary), var(--accent), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: none;
            opacity: 1; 
            transform: translateY(0); 
            background-size: 200% 200%;
            animation: gradientShift 6s ease infinite alternate;
        }

        .hero-text h2 {
            font-size: 1.8rem;
            font-weight: normal;
            min-height: 2.2rem;
            color: rgba(236, 240, 241, 0.9);
            position: relative;
            display: inline-block;
        }
        .hero-text h2::after {
            content: '';
            position: absolute;
            right: -8px;
            top: 0;
            height: 100%;
            width: 3px;
            background-color: var(--primary);
            animation: blink-caret 0.75s step-end infinite;
        }

        .hero-text p {
            font-size: 1.1rem;
            line-height: 1.6;
            margin: 1.5rem 0 2rem;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.8s ease-out 0.7s forwards, textFloat 4s ease-in-out infinite;
            color: rgba(236, 240, 241, 0.8);
            max-width: 90%;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            margin-top: 2rem;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.8s ease-out 1s forwards;
        }

        .btn {
            padding: 0.8rem 1.5rem;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                90deg,
                transparent,
                rgba(255, 255, 255, 0.2),
                transparent
            );
            transition: 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn-primary {
            background: linear-gradient(45deg, var(--primary), var(--accent));
            color: white;
            box-shadow: 0 4px 15px rgba(52, 152, 219, 0.4);
        }

        .btn-primary:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 8px 25px rgba(52, 152, 219, 0.6);
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.1);
            color: var(--light);
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-3px) scale(1.05);
        }

        .tech-icons {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
            margin-top: 3rem;
            opacity: 0;
            animation: fadeIn 1s ease-out 1.2s forwards;
            justify-content: start;
        }

        .tech-icon {
            font-size: 2rem;
            color: rgba(255, 255, 255, 0.7);
            transition: all 0.3s ease;
            position: relative;
        }

        .tech-icon::after {
            content: attr(title);
            position: absolute;
            bottom: -30px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 0.3rem 0.6rem;
            border-radius: 4px;
            font-size: 0.7rem;
            opacity: 0;
            transition: all 0.3s ease;
            white-space: nowrap;
        }

        .tech-icon:hover {
            color: var(--primary);
            transform: translateY(-5px) scale(1.1);
        }

        .tech-icon:hover::after {
            opacity: 1;
            bottom: -25px;
        }

        /* Animaciones */
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: var(--primary); }
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes textGlow {
            0% { text-shadow: 0 0 5px rgba(52, 152, 219, 0.5); }
            50% { text-shadow: 0 0 20px rgba(52, 152, 219, 0.8); }
            100% { text-shadow: 0 0 5px rgba(52, 152, 219, 0.5); }
        }

        @keyframes textFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); box-shadow: var(--shadow); }
            50% { transform: scale(1.005); box-shadow: 0 15px 40px rgba(0, 0, 0, 0.4); }
        }

        .particles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            overflow: hidden;
        }

        .particle {
            position: absolute;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 50%;
            pointer-events: none;
            filter: blur(1px);
        }

        .code-lines {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.05;
            overflow: hidden;
        }

        .code-line {
            position: absolute;
            font-family: monospace;
            color: white;
            font-size: 0.8rem;
            white-space: nowrap;
            animation: codeFlow linear infinite;
        }

        @media (max-width: 768px) {
            .hero-container {
                padding: 2rem;
            }
            
            .hero-text h1 {
                font-size: 2.5rem;
            }
            
            .hero-text h2 {
                font-size: 1.4rem;
            }
            
            .cta-buttons {
                flex-direction: column;
            }
            
            .tech-icons {
                gap: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="hero-container">
        <div class="particles" id="particles"></div>
        <div class="code-lines" id="code-lines"></div>
        <div class="hero-text">
            <h1>¡Hola! Soy David Sánchez</h1>
            <h2 id="typing-text">Desarrollador Full Stack</h2>
            <p>
                Soy una persona que adora los retos. Muy detallista y autodidacta, nunca dejo de aprender y uno de mis objetivos principales es desarrollarme profesionalmente y evolucionar en mi sector.
            </p>
            
            <div class="cta-buttons">
                <a href="#contacto" class="btn btn-primary">
                    <i class="fas fa-paper-plane"></i> Contacto
                </a>
                <a href="#proyectos" class="btn btn-secondary">
                    <i class="fas fa-code"></i> Proximamente
                </a>
            </div>
            
            <div class="tech-icons">
                <i class="fab fa-js tech-icon" title="JavaScript"></i>
                <i class="fab fa-react tech-icon" title="React"></i>
                <i class="fab fa-vuejs tech-icon" title="Vue.js"></i>
                <i class="fab fa-node-js tech-icon" title="Node.js"></i>
                <i class="fab fa-php tech-icon" title="PHP"></i>
                <i class="fab fa-laravel tech-icon" title="Laravel"></i>
                <i class="fab fa-python tech-icon" title="Python"></i>
                <i class="fas fa-database tech-icon" title="Bases de Datos"></i>
                <i class="fab fa-git-alt tech-icon" title="Git"></i>
                <i class="fab fa-linux tech-icon" title="Linux"></i>
            </div>
        </div>
    </div>

    <script>
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                
                const size = Math.random() * 4 + 1;
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                
                particle.style.left = `${Math.random() * 100}%`;
                particle.style.top = `${Math.random() * 100}%`;
                particle.style.opacity = Math.random() * 0.7 + 0.1;
                const colors = ['#3498db', '#2ecc71', '#9b59b6', '#f1c40f', '#e74c3c'];
                particle.style.background = colors[Math.floor(Math.random() * colors.length)];
                const duration = Math.random() * 20 + 10;
                const delay = Math.random() * 5;
                particle.style.animation = `float ${duration}s ease-in-out ${delay}s infinite`;
                particlesContainer.appendChild(particle);
                const keyframes = `
                    @keyframes float {
                        0% {
                            transform: translate(0, 0) rotate(0deg);
                        }
                        25% {
                            transform: translate(${Math.random() * 100 - 50}px, ${Math.random() * 100 - 50}px) rotate(90deg);
                        }
                        50% {
                            transform: translate(${Math.random() * 100 - 50}px, ${Math.random() * 100 - 50}px) rotate(180deg);
                        }
                        75% {
                            transform: translate(${Math.random() * 100 - 50}px, ${Math.random() * 100 - 50}px) rotate(270deg);
                        }
                        100% {
                            transform: translate(0, 0) rotate(360deg);
                        }
                    }
                `;
                
                const style = document.createElement('style');
                style.innerHTML = keyframes;
                document.head.appendChild(style);
            }
        }
        
        function createCodeLines() {
            const codeLinesContainer = document.getElementById('code-lines');
            const lines = [
                "const project = new Idea();",
                "function createAwesomeWeb() { ... }",
                "import { Creativity } from 'my-skills';",
                "while(!success) { tryAgain(); }",
                "git commit -m 'Mejoras increíbles'",
                "const portfolio = { projects: 42 };",
                "npm install innovation --save",
                "async function solveProblems() { ... }",
                "docker-compose up -d",
                "aws ec2 describe-instances",
                "php artisan serve",
                "vue create new-project"
            ];
            
            for (let i = 0; i < 15; i++) {
                const line = document.createElement('div');
                line.classList.add('code-line');
                line.textContent = lines[Math.floor(Math.random() * lines.length)];
                
                line.style.left = `${Math.random() * 100}%`;
                line.style.top = `${Math.random() * 100}%`;
                const duration = Math.random() * 30 + 20;
                const delay = Math.random() * 5;
                line.style.animation = `codeFlow ${duration}s linear ${delay}s infinite`;
                line.style.opacity = Math.random() * 0.1 + 0.05;
                
                codeLinesContainer.appendChild(line);
            }
        }
        
        const codeFlowKeyframes = `
            @keyframes codeFlow {
                from {
                    transform: translateX(-100%);
                }
                to {
                    transform: translateX(100vw);
                }
            }
        `;
        const codeStyle = document.createElement('style');
        codeStyle.innerHTML = codeFlowKeyframes;
        document.head.appendChild(codeStyle);
        const textElement = document.getElementById('typing-text');
        const phrases = [
            "Ingeniero Informático",
            "Desarrollador Full-Stack",
            "Programador Web",
            "Diseñador de APIs RESTful",
            "Experto en Bases de Datos",
            "Desarrollador Front-End",
            "Desarrollador Back-End",
            "Arquitecto de Software",
            "Analista de Sistemas",
            "Especialista en Next.js y React",
            "Desarrollador de Aplicaciones en Laravel",
            "Implementador de Metodologías Ágiles",
            "Automatizador de Pruebas con Selenium",
            "Administrador de Versiones en Git",
            "Optimización de Procesos Tecnológicos",
            "Integrador de Soluciones en la Nube",
            "Especialista en Node.js y Spring Boot",
            "Apasionado por el Aprendizaje Continuo"
        ];
        
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        let typingSpeed = 100;
        const prefix = "";

        function type() {
            const currentPhrase = phrases[phraseIndex];
            const fullText = prefix + currentPhrase;
            
            if (isDeleting) {
                textElement.textContent = prefix + currentPhrase.substring(0, charIndex - 1);
                charIndex--;
                typingSpeed = 50;
                if (charIndex === 0) {
                    isDeleting = false;
                    phraseIndex = (phraseIndex + 1) % phrases.length;
                    typingSpeed = 500;
                }
            } else {
                textElement.textContent = prefix + currentPhrase.substring(0, charIndex + 1);
                charIndex++;
                typingSpeed = 100 + Math.random() * 50;
                if (charIndex === currentPhrase.length) {
                    typingSpeed = 2000; 
                    isDeleting = true;
                }
            }
            
            setTimeout(type, typingSpeed);
        }

        document.addEventListener('DOMContentLoaded', () => {
            createParticles();
            createCodeLines();
            textElement.textContent = prefix;
            setTimeout(() => {
                type();
            }, 1500);
        });
    </script>
</body>
</html>
