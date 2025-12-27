<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>¡HBD Dylan!</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Bungee&family=Outfit:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --vzla-yellow: #FFD700;
            --vzla-blue: #003893;
            --vzla-red: #CE1126;
        }
        body {
            font-family: 'Outfit', sans-serif;
            background-color: #050505;
            color: white;
            touch-action: manipulation;
            -webkit-tap-highlight-color: transparent;
        }
        .bungee { font-family: 'Bungee', cursive; }
        
        .hero-gradient {
            background: radial-gradient(circle at center, #1e1b4b 0%, #050505 100%);
        }

        .floating { animation: float 4s ease-in-out infinite; }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        /* Velas del pastel */
        .candle {
            width: 20px;
            height: 65px;
            background: linear-gradient(to bottom, #FFD700, #F59E0B);
            border-radius: 6px;
            position: relative;
            cursor: pointer;
        }
        .flame {
            width: 18px;
            height: 28px;
            background: #FF5722;
            border-radius: 50% 50% 20% 20%;
            position: absolute;
            top: -30px;
            left: 1px;
            box-shadow: 0 0 20px #FF5722;
            animation: flicker 0.1s infinite alternate;
        }
        @keyframes flicker {
            from { transform: scale(1); opacity: 0.8; }
            to { transform: scale(1.1); opacity: 1; }
        }
        .flame.off { display: none; }

        .card-custom {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
        }

        /* Estilo para el canvas del juego en móvil */
        #game-canvas {
            touch-action: none;
            max-width: 100%;
            height: auto;
        }
    </style>
</head>
<body class="overflow-x-hidden">

    <!-- Música de fondo (Happy Birthday) -->
    <audio id="hbd-audio" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3" type="audio/mpeg">
    </audio>

    <!-- Botón de Música Flotante -->
    <button onclick="toggleMusic()" id="music-btn" class="fixed top-4 right-4 z-[100] bg-white/10 p-3 rounded-full border border-white/20 backdrop-blur-md">
        <span id="music-icon">🔇</span>
    </button>

    <!-- HERO SECTION -->
    <section class="min-h-screen flex flex-col items-center justify-center text-center px-4 hero-gradient relative">
        <div class="absolute inset-0 opacity-10 pointer-events-none overflow-hidden">
            <div class="absolute top-10 left-10 text-7xl rotate-12">🇻🇪</div>
            <div class="absolute bottom-20 right-10 text-7xl -rotate-12">🇵🇪</div>
        </div>

        <div class="z-10 space-y-4">
            <p class="text-yellow-400 bungee tracking-widest text-sm animate-pulse">¡HAY FIESTA SEÑORES!</p>
            <h1 class="text-6xl font-black leading-tight uppercase">
                FELIZ CUMPLE <br>
                <span class="text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 via-white to-red-500">DYLAN</span>
            </h1>
            <p class="text-gray-400 text-lg max-w-xs mx-auto italic">
                El chamo más crack está de nivel hoy. ¡Dale al botón para activar el bonche!
            </p>
            
            <button onclick="activateApp()" id="activate-btn" class="mt-8 bg-white text-black font-black px-8 py-5 rounded-2xl text-xl shadow-xl active:scale-90 transition-transform">
                ¡EMPEZAR RUMBA! 🚀
            </button>
        </div>
    </section>

    <!-- CLASSIC DYLAN JOKES -->
    <section class="py-16 px-4 space-y-6">
        <h2 class="text-center bungee text-2xl text-blue-400">Status de Dylan Hoy:</h2>
        
        <div class="grid grid-cols-1 gap-4">
            <div class="card-custom p-6 rounded-3xl flex items-start space-x-4">
                <div class="text-3xl">🏃‍♂️</div>
                <div>
                    <h3 class="font-bold text-yellow-400">Puntualidad Dylan</h3>
                    <p class="text-gray-400 text-sm">"Mano, ya voy llegando" = Apenas se está quitando la toalla.</p>
                </div>
            </div>
            
            <div class="card-custom p-6 rounded-3xl flex items-start space-x-4">
                <div class="text-3xl">🫓</div>
                <div>
                    <h3 class="font-bold text-red-500">El DNI ya viene</h3>
                    <p class="text-gray-400 text-sm">Próximamente Dylan será un ciudadano perucho legal. ¡Falta poco!</p>
                </div>
            </div>
        </div>
    </section>

    <!-- INTERACTIVE CAKE -->
    <section class="py-20 px-4 flex flex-col items-center justify-center bg-white/5 rounded-[3rem] mx-2">
        <h2 class="bungee text-2xl mb-12 text-center">¡Dylan, sopla tus velas! 🕯️</h2>
        
        <div class="relative">
            <!-- Pastel gigante -->
            <div class="w-64 h-36 bg-white rounded-t-[2.5rem] shadow-2xl flex items-center justify-center overflow-hidden border-b-8 border-red-500">
                <span class="text-slate-900 font-black text-6xl bungee z-10 tracking-tighter">DYLAN</span>
                <div class="absolute inset-0 bg-yellow-400/10 flex items-center justify-center">
                    <span class="opacity-10 text-6xl">🎂</span>
                </div>
            </div>

            <!-- Velas -->
            <div class="flex space-x-8 absolute -top-12 left-1/2 -translate-x-1/2">
                <div class="candle" onclick="blow(this)"><div class="flame"></div></div>
                <div class="candle" onclick="blow(this)"><div class="flame"></div></div>
                <div class="candle" onclick="blow(this)"><div class="flame"></div></div>
            </div>
        </div>
        <p class="mt-12 text-gray-500 text-sm italic">Toca las llamas para pedir un deseo</p>
    </section>

    <!-- MINI GAME -->
    <section class="py-20 px-4 flex flex-col items-center">
        <h2 class="text-3xl font-black mb-2">RETO DEL CHAMO 🎮</h2>
        <p class="text-gray-400 mb-8 text-center text-sm">Atrapa los ingredientes del pabellón y el ceviche antes que Dylan llegue tarde.</p>
        
        <div class="relative w-full max-w-sm">
            <canvas id="game-canvas" width="400" height="500" class="w-full bg-slate-900 rounded-[2rem] border-2 border-white/10 shadow-2xl"></canvas>
            <div id="game-ui" class="absolute inset-0 flex flex-col items-center justify-center bg-black/80 rounded-[2rem] backdrop-blur-sm">
                <p id="high-score" class="text-3xl font-bold mb-6">Puntos: 0</p>
                <button onclick="startGame()" class="bg-yellow-400 text-black px-10 py-4 rounded-full font-black text-lg">¡DALE DYLAN!</button>
            </div>
        </div>
    </section>

    <!-- PHOTO MEMORY -->
    <section class="py-20 px-4 bg-white text-black rounded-t-[3rem]">
        <div class="max-w-md mx-auto">
            <div class="text-center mb-10">
                <span class="text-xs font-black bg-blue-600 text-white px-3 py-1 rounded-full tracking-widest uppercase">Un Día Épico</span>
                <h2 class="text-4xl font-black mt-2 bungee italic">CON LAS CHICAS Y EL TUTO</h2>
            </div>

            <div class="relative p-2 bg-slate-950 rounded-[2rem] shadow-2xl transform rotate-1">
                <img src="https://cdn.discordapp.com/attachments/1392377430030811289/1454307662559969412/Screenshot_2025-12-26-21-49-26-245_com.instagram.android.jpg?ex=69509d0e&is=694f4b8e&hm=b15565d45aab6f23fe870b96107e9df6f2048403a7b21c893ef1133adcdb9ce5&" 
                     alt="Dylan con sus amigas y Tuto" 
                     class="rounded-[1.8rem] w-full h-auto">
            </div>

            <div class="mt-12 text-center space-y-4 px-2">
                <p class="text-xl font-medium leading-tight">
                    Qué buena foto, Dylan. Se nota que la pasaron brutal con las chicas y que el <span class="font-black text-blue-600">Tuto</span> no podía faltar en esa salida.
                </p>
                <p class="text-gray-500 italic text-sm">
                    Momentos así son los que valen oro. ¡Que se repitan muchos más este año!
                </p>
            </div>
        </div>
    </section>

    <footer class="py-12 text-center opacity-30">
        <p class="text-xs bungee">HBD DYLAN - EL CHAMO - 2025</p>
    </footer>

    <!-- MODAL PERSONALIZADO -->
    <div id="modal" class="fixed inset-0 z-[200] hidden items-center justify-center bg-black/95 p-6 backdrop-blur-xl">
        <div class="text-center max-w-sm w-full">
            <div id="modal-icon" class="text-7xl mb-6">🥳</div>
            <h3 id="modal-title" class="text-3xl font-black mb-2 uppercase"></h3>
            <p id="modal-body" class="text-gray-400 mb-8"></p>
            <button onclick="closeModal()" class="w-full bg-white text-black font-black py-4 rounded-xl text-lg active:scale-95 transition-transform">¡VAMOS!</button>
        </div>
    </div>

    <script>
        const audio = document.getElementById('hbd-audio');
        let musicActive = false;

        function activateApp() {
            if(!musicActive) toggleMusic();
            startConfetti();
            document.getElementById('activate-btn').innerText = "¡FELICIDADES!";
            // Scroll suave a las bromas
            window.scrollBy({ top: 300, behavior: 'smooth' });
        }

        function toggleMusic() {
            if (musicActive) {
                audio.pause();
                document.getElementById('music-icon').innerText = "🔇";
            } else {
                audio.play().catch(e => console.log("Click needed for audio"));
                document.getElementById('music-icon').innerText = "🔊";
            }
            musicActive = !musicActive;
        }

        function startConfetti() {
            confetti({
                particleCount: 150,
                spread: 70,
                origin: { y: 0.6 },
                colors: ['#FFD700', '#003893', '#CE1126']
            });
            showModal("¡QUÉ NIVEL DYLAN!", "Tu cumple ha comenzado oficialmente. ¡Pásalo increíble, mano!", "🔥");
        }

        function blow(el) {
            const flame = el.querySelector('.flame');
            if (!flame.classList.contains('off')) {
                flame.classList.add('off');
                confetti({ particleCount: 20, spread: 40, origin: { y: 0.7 } });
                
                const allOff = Array.from(document.querySelectorAll('.flame')).every(f => f.classList.contains('off'));
                if (allOff) {
                    setTimeout(() => {
                        showModal("DESEO GUARDADO", "Dylan, que este año logres todo lo que te propongas (y que llegues temprano a la próxima).", "✨");
                    }, 500);
                }
            }
        }

        function showModal(title, body, icon) {
            document.getElementById('modal-title').innerText = title;
            document.getElementById('modal-body').innerText = body;
            document.getElementById('modal-icon').innerText = icon;
            const modal = document.getElementById('modal');
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }

        function closeModal() {
            document.getElementById('modal').classList.add('hidden');
            document.getElementById('modal').classList.remove('flex');
        }

        // --- GAME ENGINE ---
        const canvas = document.getElementById('game-canvas');
        const ctx = canvas.getContext('2d');
        const ui = document.getElementById('game-ui');
        let score = 0;
        let gameActive = false;
        let foods = [];
        const items = ['🫓', '🍲', '🥑', '🧀', '🍔'];

        class Food {
            constructor() {
                this.x = Math.random() * (canvas.width - 60) + 30;
                this.y = -50;
                this.emoji = items[Math.floor(Math.random() * items.length)];
                this.speed = 4 + Math.random() * 4;
            }
            update() { this.y += this.speed; }
            draw() {
                ctx.font = '50px serif';
                ctx.textAlign = 'center';
                ctx.fillText(this.emoji, this.x, this.y);
            }
        }

        function startGame() {
            score = 0;
            foods = [];
            gameActive = true;
            ui.style.display = 'none';
            gameLoop();
        }

        function gameLoop() {
            if (!gameActive) return;
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            if (Math.random() < 0.05) foods.push(new Food());

            for (let i = foods.length - 1; i >= 0; i--) {
                const f = foods[i];
                f.update();
                f.draw();

                if (f.y > canvas.height) {
                    gameActive = false;
                    ui.style.display = 'flex';
                    document.getElementById('high-score').innerText = `Puntos: ${score}`;
                    showModal("¡CASI, DYLAN!", `Hiciste ${score} puntos. ¡Dale otra vez!`, "🥗");
                    return;
                }
            }
            requestAnimationFrame(gameLoop);
        }

        function tap(ex, ey) {
            if (!gameActive) return;
            const rect = canvas.getBoundingClientRect();
            const x = (ex - rect.left) * (canvas.width / rect.width);
            const y = (ey - rect.top) * (canvas.height / rect.height);

            for (let i = foods.length - 1; i >= 0; i--) {
                const f = foods[i];
                const d = Math.sqrt((x - f.x)**2 + (y - f.y)**2);
                if (d < 50) {
                    foods.splice(i, 1);
                    score++;
                    document.getElementById('high-score').innerText = `Puntos: ${score}`;
                    break;
                }
            }
        }

        canvas.addEventListener('mousedown', e => tap(e.clientX, e.clientY));
        canvas.addEventListener('touchstart', e => {
            e.preventDefault();
            tap(e.touches[0].clientX, e.touches[0].clientY);
        });

    </script>
</body>
</html>
