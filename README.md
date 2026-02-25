<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arda Eren | Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.15.1/devicon.min.css">
    
    <style>
        :root {
            --bg-color: #0D1117;
            --text-color: #C9D1D9;
            --accent-color: #6366F1;
            --accent-glow: rgba(99, 102, 241, 0.4);
            --card-bg: rgba(22, 27, 34, 0.7);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* --- YENİ: Particles.js Arka Planı İçin --- */
        #particles-js {
            position: fixed;
            width: 100vw;
            height: 100vh;
            top: 0;
            left: 0;
            z-index: -1; /* Bütün içeriğin arkasında kalmasını sağlar */
        }

        /* Gelişmiş Scroll Animasyon Sınıfları */
        .hidden-left {
            opacity: 0;
            transform: translateX(-100px);
            transition: all 0.8s cubic-bezier(0.25, 1, 0.5, 1);
        }
        
        .hidden-right {
            opacity: 0;
            transform: translateX(100px);
            transition: all 0.8s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .hidden-up {
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s cubic-bezier(0.25, 1, 0.5, 1);
        }
        
        .show {
            opacity: 1;
            transform: translate(0, 0);
        }

        /* Layout */
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 0 20px;
            position: relative; /* İçeriğin parçacıkların üstünde kalması için */
            z-index: 1;
        }

        section {
            padding: 100px 0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        h2 {
            font-size: 2.5rem;
            color: #fff;
            margin-bottom: 50px;
            text-align: center;
            position: relative;
        }

        h2::after {
            content: '';
            width: 60px;
            height: 4px;
            background: var(--accent-color);
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        /* Hero Section */
        .hero {
            text-align: center;
            align-items: center;
        }

        .hero h1 {
            font-size: 4rem;
            color: #fff;
            margin-bottom: 10px;
            background: linear-gradient(90deg, #6366F1, #20BEFF);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-subtitle {
            font-size: 1.5rem;
            margin-bottom: 30px;
            font-weight: 300;
        }

        .social-links {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 30px;
        }

        .social-links a {
            color: var(--text-color);
            font-size: 1.8rem;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            display: flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--card-bg);
            text-decoration: none;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .social-links a:hover {
            color: #fff;
            background: var(--accent-color);
            box-shadow: 0 0 20px var(--accent-glow);
            transform: translateY(-8px) scale(1.1);
        }

        /* About Section */
        .about-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .about-card {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.05);
            backdrop-filter: blur(10px);
            transition: all 0.4s ease;
        }

        .about-card:hover {
            transform: translateY(-10px);
            border-color: rgba(99, 102, 241, 0.5);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        .about-card i {
            font-size: 2rem;
            color: var(--accent-color);
            margin-bottom: 15px;
        }

        /* Tech Stack Arkadan Belirme Efektleri */
        .tech-grid {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 40px;
            margin-top: 30px;
        }

        .tech-wrapper {
            position: relative;
        }

        .tech-pop-icon {
            position: absolute;
            font-size: 2.5rem;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            opacity: 0;
            z-index: 0;
            transition: all 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            pointer-events: none;
        }

        .tech-card {
            display: flex;
            align-items: center;
            gap: 15px;
            background: var(--bg-color);
            padding: 15px 35px;
            border-radius: 50px;
            border: 1px solid rgba(255,255,255,0.1);
            font-size: 1.2rem;
            font-weight: 600;
            cursor: pointer;
            position: relative;
            z-index: 1;
            transition: all 0.4s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .tech-card i {
            font-size: 1.8rem;
            transition: transform 0.4s ease;
        }

        .tech-wrapper:hover .tech-card {
            transform: translateY(-5px);
            background: var(--card-bg);
            border-color: var(--accent-color);
            box-shadow: 0 10px 25px var(--accent-glow);
            color: #fff;
        }

        .tech-wrapper:hover .tech-card i {
            transform: rotate(360deg);
        }

        .tech-wrapper:hover .tech-pop-icon {
            transform: translate(-50%, -130%) scale(1);
            opacity: 1;
        }
        
        .tech-wrapper:hover .python-pop { transform: translate(-50%, -130%) scale(1) rotate(-15deg); }
        .tech-wrapper:hover .csharp-pop { transform: translate(-50%, -130%) scale(1) rotate(15deg); }
        .tech-wrapper:hover .js-pop { transform: translate(-50%, -130%) scale(1) rotate(-10deg); }

    </style>
</head>
<body>

    <div id="particles-js"></div>

    <div class="container">
        <section class="hero hidden-up">
            <h1>Arda Eren 👋</h1>
            <div class="hero-subtitle">
                <span id="typewriter"></span>
            </div>
            <p>Developer | AI Enthusiast</p>
            
            <div class="social-links">
                <a href="https://www.linkedin.com/in/arda-eren-7030422a2/" target="_blank" title="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
                <a href="https://huggingface.co/ArdaEren2401" target="_blank" title="HuggingFace">🤗</a>
                <a href="https://www.kaggle.com/ardaeren2401" target="_blank" title="Kaggle"><i class="fab fa-kaggle"></i></a>
            </div>
        </section>

        <section>
            <h2 class="hidden-up">Hakkımda</h2>
            <div class="about-grid">
                <div class="about-card hidden-left" style="transition-delay: 100ms;">
                    <i class="fas fa-graduation-cap"></i>
                    <h3>Eğitim</h3>
                    <p>Ankara Medipol Üniversitesi'nde Bilgisayar Programcılığı okuyorum. Geleceğin Bilgisayar Mühendisi olma yolunda DGS çalışmalarıma aralıksız devam ediyorum.</p>
                </div>
                <div class="about-card hidden-up" style="transition-delay: 300ms;">
                    <i class="fas fa-brain"></i>
                    <h3>Yapay Zeka & Veri Bilimi</h3>
                    <p>Yapay Zeka (AI), Makine Öğrenmesi ve Veri Bilimi (Data Science) alanlarında kendimi sürekli geliştiriyorum. Verilerden anlamlı sonuçlar çıkarmak ve otomasyon süreçleri oluşturmak en büyük tutkum.</p>
                </div>
                <div class="about-card hidden-right" style="transition-delay: 500ms;">
                    <i class="fas fa-gamepad"></i>
                    <h3>İlgi Alanları</h3>
                    <p>Kod yazmaktan ve yeni algoritmalar öğrenmekten arta kalan zamanlarda RDR2, The Last of Us ve God of War gibi harika atmosfere sahip hikaye odaklı oyunların dünyasında kaybolmayı seviyorum.</p>
                </div>
            </div>
        </section>

        <section>
            <h2 class="hidden-up">Diller ve Teknolojiler</h2>
            <div class="tech-grid">
                
                <div class="tech-wrapper hidden-left" style="transition-delay: 200ms;">
                    <span class="tech-pop-icon python-pop">🐍</span>
                    <div class="tech-card">
                        <i class="devicon-python-plain colored"></i>
                        Python
                    </div>
                </div>

                <div class="tech-wrapper hidden-up" style="transition-delay: 400ms;">
                    <span class="tech-pop-icon csharp-pop">⚙️</span>
                    <div class="tech-card">
                        <i class="devicon-csharp-plain colored"></i>
                        C#
                    </div>
                </div>

                <div class="tech-wrapper hidden-right" style="transition-delay: 600ms;">
                    <span class="tech-pop-icon js-pop">⚡</span>
                    <div class="tech-card">
                        <i class="devicon-javascript-plain colored"></i>
                        JavaScript
                    </div>
                </div>

            </div>
        </section>
    </div>

    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>

    <script>
        // --- YENİ: Particles.js Çok Sade Konfigürasyonu ---
        particlesJS("particles-js", {
            "particles": {
                "number": {
                    "value": 40, // Çok kalabalık olmaması için az sayıda tutuldu
                    "density": { "enable": true, "value_area": 800 }
                },
                "color": { "value": "#6366F1" }, // Aksan rengimizle uyumlu
                "shape": { "type": "circle" },
                "opacity": {
                    "value": 0.2, // Çok saydam, göz yormayacak
                    "random": false
                },
                "size": {
                    "value": 3,
                    "random": true
                },
                "line_linked": {
                    "enable": true,
                    "distance": 150,
                    "color": "#6366F1",
                    "opacity": 0.15,
                    "width": 1
                },
                "move": {
                    "enable": true,
                    "speed": 1.5, // Yavaş ve sakin bir hareket
                    "direction": "none",
                    "random": true,
                    "straight": false,
                    "out_mode": "out",
                    "bounce": false
                }
            },
            "interactivity": {
                "detect_on": "canvas",
                "events": {
                    "onhover": { "enable": true, "mode": "grab" }, // Mouse'a doğru ağ örer
                    "onclick": { "enable": true, "mode": "push" }, // Tıklayınca parçacık ekler
                    "resize": true
                },
                "modes": {
                    "grab": { "distance": 150, "line_linked": { "opacity": 0.4 } },
                    "push": { "particles_nb": 3 }
                }
            },
            "retina_detect": true
        });

        // Typewriter Effect
        const textArray = ["Building the future with code 🚀", "Passionate about AI & Data Science 🤖"];
        let textIndex = 0;
        let charIndex = 0;
        const speed = 100;
        const delayBetweenTexts = 2000;
        const typewriterElement = document.getElementById("typewriter");

        function typeWriter() {
            if (charIndex < textArray[textIndex].length) {
                typewriterElement.innerHTML += textArray[textIndex].charAt(charIndex);
                charIndex++;
                setTimeout(typeWriter, speed);
            } else {
                setTimeout(eraseText, delayBetweenTexts);
            }
        }

        function eraseText() {
            if (charIndex > 0) {
                typewriterElement.innerHTML = textArray[textIndex].substring(0, charIndex - 1);
                charIndex--;
                setTimeout(eraseText, speed / 2);
            } else {
                textIndex = (textIndex + 1) % textArray.length;
                setTimeout(typeWriter, speed);
            }
        }

        document.addEventListener("DOMContentLoaded", function() {
            setTimeout(typeWriter, speed);
        });

        // Gelişmiş Scroll Animation (Intersection Observer)
        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('show');
                }
            });
        }, {
            threshold: 0.1,
            rootMargin: "0px 0px -50px 0px"
        });

        const hiddenElements = document.querySelectorAll('.hidden-left, .hidden-right, .hidden-up');
        hiddenElements.forEach((el) => observer.observe(el));
    </script>
</body>
</html>
