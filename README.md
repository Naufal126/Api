# ✨ Portofolio Interaktif Naufal

![Header GIF](https://media.giphy.com/media/3o7TKP8F1Ztq3rZQ8U/giphy.gif)

> Demo portofolio interaktif dengan efek particle dan background gradient, semuanya **HTML + CSS + JS di satu file**!

---

## 🚀 Fitur

- 🌈 Background gradient & floating particles  
- 📱 Responsive di desktop & mobile  
- ⚡ Cepat & ringan  
- 💬 Integrasi media sosial (WhatsApp, Instagram)  
- 🎨 UI aesthetic & modern  

---

## 💻 Kode HTML + CSS + JS (Gabungan)

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Portofolio Naufal</title>
    <style>
        /* CSS langsung di sini */
        body {
            background: linear-gradient(to right, #8e2de2, #4a00e0);
            font-family: 'Poppins', sans-serif;
            margin: 0;
            overflow: hidden;
        }
        header {
            text-align: center;
            color: white;
            padding: 100px 20px 50px 20px;
        }
        header h1 {
            font-size: 3rem;
            animation: bounce 2s infinite;
        }
        header p {
            font-size: 1.2rem;
            color: #eee;
        }
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        canvas {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: -1;
        }
        section#contact a {
            display: inline-block;
            margin: 10px;
            padding: 10px 20px;
            color: white;
            background: #ff6b81;
            border-radius: 10px;
            text-decoration: none;
            font-weight: bold;
            transition: 0.3s;
        }
        section#contact a:hover {
            background: #ff4757;
        }
    </style>
</head>
<body>
    <header>
        <h1>Halo, saya Naufal 👋</h1>
        <p>Portofolio interaktif dengan efek keren!</p>
    </header>

    <section id="contact">
        <a href="https://wa.me/628xxxxxx" target="_blank">WhatsApp</a>
        <a href="https://instagram.com/username" target="_blank">Instagram</a>
    </section>

    <canvas id="particleCanvas"></canvas>

    <script>
        // JavaScript langsung di sini
        const canvas = document.getElementById('particleCanvas');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let particles = [];
        for(let i = 0; i < 100; i++) {
            particles.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                size: Math.random() * 3 + 1,
                speedX: Math.random() * 1 - 0.5,
                speedY: Math.random() * 1 - 0.5
            });
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                ctx.fillStyle = 'white';
                ctx.fill();
                p.x += p.speedX;
                p.y += p.speedY;

                if(p.x < 0 || p.x > canvas.width) p.speedX *= -1;
                if(p.y < 0 || p.y > canvas.height) p.speedY *= -1;
            });
            requestAnimationFrame(animate);
        }

        animate();

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
