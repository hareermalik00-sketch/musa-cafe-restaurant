
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Dearest Teacher! ✨📚</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>

    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600;700&family=Playfair+Display:ital,wght@0,500;0,700;1,400;1,600&family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <!-- Three.js CDN -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

    <!-- Canvas Confetti CDN -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        pastel: {
                            cream: '#FFFBF7',
                            blush: '#FCE7F1',
                            pink: '#FBCFE8',
                            lavender: '#F3E8FF',
                            purple: '#E9D5FF',
                            mint: '#E6F4EA',
                            peach: '#FFE8D6',
                            gold: '#D97706',
                            rose: '#E11D48',
                            dark: '#3B322C',
                            muted: '#6E6259'
                        }
                    },
                    fontFamily: {
                        sans: ['Poppins', 'sans-serif'],
                        serif: ['Playfair Display', 'serif'],
                        script: ['Dancing Script', 'cursive']
                    }
                }
            }
        }
    </script>

    <style>
        /* Global Smooth Scroll */
        html {
            scroll-behavior: smooth;
        }

        body {
            background-color: #FFFBF7;
            color: #3B322C;
            font-family: 'Poppins', sans-serif;
            overflow-x: hidden;
        }

        /* Fixed Three.js Background Canvas */
        #three-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
            pointer-events: none;
        }

        /* Glassmorphism Styling */
        .glass-card {
            background: rgba(255, 255, 255, 0.75);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.9);
            box-shadow: 0 10px 30px -10px rgba(225, 29, 72, 0.08);
        }

        .glass-card-hover {
            transition: all 0.4s ease;
        }
        .glass-card-hover:hover {
            transform: translateY(-6px);
            box-shadow: 0 20px 35px -10px rgba(225, 29, 72, 0.15);
        }

        /* 3D Flip Card Effect */
        .perspective-1000 {
            perspective: 1000px;
        }
        .transform-style-3d {
            transform-style: preserve-3d;
            transition: transform 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .flipped {
            transform: rotateY(180deg);
        }
        .backface-hidden {
            backface-visibility: hidden;
        }
        .rotate-y-180 {
            transform: rotateY(180deg);
        }

        /* Candle Flame Animation */
        @keyframes flicker {
            0%, 100% { transform: scale(1) rotate(-1deg); opacity: 0.9; }
            25% { transform: scale(1.1) rotate(1deg); opacity: 1; }
            50% { transform: scale(0.95) rotate(-2deg); opacity: 0.85; }
            75% { transform: scale(1.15) rotate(2deg); opacity: 1; }
        }
        .flame-anim {
            animation: flicker 0.8s infinite ease-in-out;
            transform-origin: bottom center;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #FFFBF7;
        }
        ::-webkit-scrollbar-thumb {
            background: #FBCFE8;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #F472B6;
        }
    </style>
</head>
<body class="relative min-h-screen">

    <!-- 3D Background Canvas -->
    <canvas id="three-canvas"></canvas>

    <!-- Navigation Bar -->
    <nav class="sticky top-0 z-50 glass-card border-b border-pink-100/60 px-4 sm:px-8 py-3 transition-all duration-300">
        <div class="max-w-7xl mx-auto flex items-center justify-between">
            <a href="#hero" class="font-script text-2xl sm:text-3xl font-bold text-pastel-rose flex items-center gap-2">
                <i class="fa-solid fa-feather-pointed text-pink-400"></i> Best Teacher Ever
            </a>
            
            <div class="hidden lg:flex items-center space-x-6 text-xs sm:text-sm font-medium text-pastel-muted">
                <a href="#letter" class="hover:text-pastel-rose transition-colors">Letter</a>
                <a href="#treasure" class="hover:text-pastel-rose transition-colors">Literary Quotes</a>
                <a href="#timeline" class="hover:text-pastel-rose transition-colors">Class Moments</a>
                <a href="#vocab" class="hover:text-pastel-rose transition-colors">Vocab 3D Cards</a>
                <a href="#wishes" class="hover:text-pastel-rose transition-colors">Wish Wall</a>
                <a href="#quiz" class="hover:text-pastel-rose transition-colors">Fun Quiz</a>
                <a href="#unboxing" class="hover:text-pastel-rose transition-colors">Unboxing</a>
            </div>

            <div class="flex items-center gap-3">
                <!-- Audio Toggle Button -->
                <button id="audio-toggle" onclick="toggleAudio()" class="w-9 h-9 rounded-full bg-pastel-blush hover:bg-pastel-pink text-pastel-rose flex items-center justify-center transition-all shadow-sm">
                    <i id="audio-icon" class="fa-solid fa-music"></i>
                </button>
                <button onclick="triggerEpicConfetti()" class="px-4 py-2 text-xs sm:text-sm font-semibold text-rose-700 bg-gradient-to-r from-pink-200 to-purple-200 hover:from-pink-300 hover:to-purple-300 rounded-full transition-all duration-300 shadow-sm flex items-center gap-2">
                    <i class="fa-solid fa-wand-magic-sparkles"></i> Celebrate!
                </button>
            </div>
        </div>
    </nav>

    <!-- SECTION 1: HERO SECTION -->
    <section id="hero" class="relative min-h-[90vh] flex flex-col items-center justify-center text-center px-4 py-16 max-w-5xl mx-auto z-10">
        <div class="inline-flex items-center gap-2 px-4 py-1.5 bg-pastel-blush text-pastel-rose rounded-full text-xs sm:text-sm font-semibold mb-6 shadow-sm border border-pink-200">
            <i class="fa-solid fa-sparkles"></i> Dedicated to Our Incredible English Teacher
        </div>

        <h1 class="font-serif text-4xl sm:text-6xl md:text-7xl font-bold text-pastel-dark leading-tight mb-6">
            Happy Birthday, <br/>
            <span class="font-script text-pastel-rose font-normal text-5xl sm:text-7xl md:text-8xl block mt-2">Respected Ma'am! ✨</span>
        </h1>

        <p class="text-base sm:text-xl text-pastel-muted max-w-2xl mx-auto mb-10 font-light leading-relaxed">
            Thank you for inspiring us with the beauty of literature, teaching us the power of eloquence, and guiding us with endless warmth and wisdom!
        </p>

        <!-- 3D Interactive Cake Header Component -->
        <div class="glass-card p-6 sm:p-8 rounded-3xl border border-pink-200 max-w-lg w-full shadow-lg relative overflow-hidden">
            <p class="text-xs font-bold uppercase tracking-widest text-pink-500 mb-2">Interactive Cake & Candle</p>
            <p class="text-xs text-pastel-muted mb-6">Click or tap on the candle flame to blow it out and unlock the celebration!</p>

            <!-- Virtual 3D Candle & Cake Graphic -->
            <div class="relative w-48 h-44 mx-auto flex flex-col items-center justify-end mb-4">
                <!-- Candle Container -->
                <div id="candle-wrapper" class="cursor-pointer relative z-20 flex flex-col items-center group" onclick="blowCandle()">
                    <!-- Flame -->
                    <div id="cake-flame" class="w-5 h-7 bg-amber-400 rounded-full flame-anim shadow-[0_0_20px_#f59e0b] border border-yellow-200"></div>
                    <!-- Wick -->
                    <div class="w-1 h-2.5 bg-gray-700"></div>
                    <!-- Candle Body -->
                    <div class="w-4 h-10 bg-gradient-to-r from-pink-300 via-white to-pink-300 rounded-t-sm shadow-inner"></div>
                </div>

                <!-- Cake Top Layer -->
                <div class="w-36 h-10 bg-pastel-blush rounded-t-2xl border-b-4 border-pink-200 relative flex items-center justify-around px-2 shadow-inner">
                    <div class="w-3.5 h-3.5 rounded-full bg-rose-400 -mt-6 shadow"></div>
                    <div class="w-3.5 h-3.5 rounded-full bg-rose-400 -mt-6 shadow"></div>
                    <div class="w-3.5 h-3.5 rounded-full bg-rose-400 -mt-6 shadow"></div>
                </div>

                <!-- Cake Middle Layer -->
                <div class="w-44 h-12 bg-pastel-cream rounded-t-lg border-b-4 border-pink-100 relative flex items-center justify-center">
                    <span class="font-script text-pastel-rose font-bold text-base">Happy Birthday!</span>
                </div>

                <!-- Cake Bottom Layer -->
                <div class="w-52 h-12 bg-pink-100 rounded-t-lg border-b-8 border-pink-300 shadow-md"></div>
                <!-- Plate -->
                <div class="w-60 h-3 bg-gray-200/90 rounded-full shadow-lg"></div>
            </div>

            <div id="candle-message" class="text-xs sm:text-sm font-semibold text-rose-600">
                🔥 The candle is lit! Make a birthday wish & tap the flame!
            </div>
        </div>
    </section>

    <!-- SECTION 2: HEARTFELT TRIBUTE LETTER -->
    <section id="letter" class="py-20 px-4 sm:px-6 max-w-4xl mx-auto z-10 relative">
        <div class="text-center mb-10">
            <span class="text-xs uppercase tracking-widest text-pink-500 font-bold">A Heartfelt Tribute</span>
            <h2 class="font-serif text-3xl sm:text-5xl font-bold text-pastel-dark mt-1">A Letter of Gratitude</h2>
            <div class="w-16 h-1 bg-pastel-pink mx-auto mt-3 rounded-full"></div>
        </div>

        <div class="glass-card p-8 sm:p-14 rounded-3xl border border-pink-200/70 shadow-xl relative bg-gradient-to-br from-white/90 via-pink-50/20 to-purple-50/20">
            <div class="absolute top-6 right-6 text-pink-200/50 text-7xl select-none">
                <i class="fa-solid fa-envelope-open-text"></i>
            </div>

            <div class="font-serif text-pastel-dark space-y-6 text-base sm:text-lg leading-relaxed relative z-10">
                <p class="font-script text-3xl sm:text-4xl text-pastel-rose font-bold">Respected Ma'am,</p>
                <p>
                    On this very special occasion of your birthday, I wanted to create a small digital corner filled with appreciation, respect, and warmth to show you how much you mean to us as our mentor and teacher.
                </p>
                <p>
                    English was just another subject until we joined your classroom. The way you make words feel alive, the passion with which you share literature, and the gentle patience you show every single day turned learning into a joyful experience. You didn't just teach us grammar and vocabulary; you taught us how to express our thoughts with confidence and clarity.
                </p>
                <p>
                    Thank you for always encouraging us, for correcting our tiny blunders with a warm smile, and for being such a wonderful role model. May your year ahead be blessed with infinite joy, serenity, good health, and all the happiness you bring into our lives!
                </p>
                <div class="pt-8 border-t border-pink-100/80 text-right">
                    <p class="font-script text-3xl text-pastel-rose font-bold">With utmost respect & admiration,</p>
                    <p class="text-xs sm:text-sm font-sans text-pastel-muted font-semibold mt-1">Your Devoted Student 🌸</p>
                </div>
            </div>
        </div>
    </section>

    <!-- SECTION 3: LITERARY TREASURE BOX -->
    <section id="treasure" class="py-20 px-4 sm:px-6 max-w-6xl mx-auto z-10 relative">
        <div class="text-center mb-12">
            <span class="text-xs uppercase tracking-widest text-purple-500 font-bold">Literary Aesthetic</span>
            <h2 class="font-serif text-3xl sm:text-4xl font-bold text-pastel-dark mt-1">Literary Treasure Box</h2>
            <p class="text-xs sm:text-sm text-pastel-muted mt-2">Timeless quotes curated for an extraordinary teacher</p>
            <div class="w-16 h-1 bg-pastel-purple mx-auto mt-3 rounded-full"></div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <!-- Quote Card 1 -->
            <div class="glass-card p-8 rounded-3xl border border-purple-200/80 glass-card-hover flex flex-col justify-between">
                <div>
                    <i class="fa-solid fa-quote-left text-3xl text-purple-300 mb-4 block"></i>
                    <p class="font-serif italic text-base text-pastel-dark leading-relaxed mb-6">
                        "The art of teaching is the art of assisting discovery."
                    </p>
                </div>
                <div>
                    <span class="text-xs font-bold text-purple-700 bg-purple-100 px-3 py-1 rounded-full">— Mark Van Doren</span>
                </div>
            </div>

            <!-- Quote Card 2 -->
            <div class="glass-card p-8 rounded-3xl border border-pink-200/80 glass-card-hover flex flex-col justify-between">
                <div>
                    <i class="fa-solid fa-quote-left text-3xl text-pink-300 mb-4 block"></i>
                    <p class="font-serif italic text-base text-pastel-dark leading-relaxed mb-6">
                        "Words are, in my not-so-humble opinion, our most inexhaustible source of magic."
                    </p>
                </div>
                <div>
                    <span class="text-xs font-bold text-rose-700 bg-pink-100 px-3 py-1 rounded-full">— J.K. Rowling</span>
                </div>
            </div>

            <!-- Quote Card 3 -->
            <div class="glass-card p-8 rounded-3xl border border-amber-200/80 glass-card-hover flex flex-col justify-between">
                <div>
                    <i class="fa-solid fa-quote-left text-3xl text-amber-300 mb-4 block"></i>
                    <p class="font-serif italic text-base text-pastel-dark leading-relaxed mb-6">
                        "There is no frigate like a book to take us lands away."
                    </p>
                </div>
                <div>
                    <span class="text-xs font-bold text-amber-800 bg-amber-100 px-3 py-1 rounded-full">— Emily Dickinson</span>
                </div>
            </div>
        </div>
    </section>

    <!-- SECTION 4: A DAY IN ENGLISH CLASS TIMELINE -->
    <section id="timeline" class="py-20 px-4 sm:px-6 max-w-4xl mx-auto z-10 relative">
        <div class="text-center mb-14">
            <span class="text-xs uppercase tracking-widest text-emerald-600 font-bold">Classroom Memories</span>
            <h2 class="font-serif text-3xl sm:text-4xl font-bold text-pastel-dark mt-1">A Day in English Class</h2>
            <div class="w-16 h-1 bg-pastel-mint mx-auto mt-3 rounded-full"></div>
        </div>

        <div class="relative border-l-2 border-emerald-200/80 ml-4 sm:ml-32 space-y-10">
            <!-- Timeline Item 1 -->
            <div class="relative pl-8 sm:pl-10">
                <div class="absolute -left-[17px] top-1.5 w-8 h-8 rounded-full bg-pastel-mint border-2 border-emerald-400 flex items-center justify-center text-emerald-700 text-xs shadow-sm">
                    <i class="fa-solid fa-sun"></i>
                </div>
                <div class="glass-card p-6 rounded-2xl border border-emerald-100 shadow-sm">
                    <span class="text-xs font-bold text-emerald-700 bg-emerald-100 px-2.5 py-0.5 rounded-full">8:30 AM • The Warm Greeting</span>
                    <h3 class="font-serif text-lg font-bold text-pastel-dark mt-2">A Welcoming Smile</h3>
                    <p class="text-xs sm:text-sm text-pastel-muted mt-1 leading-relaxed">
                        Class starts with your bright greeting that instantly sets a positive and warm mood for the entire day.
                    </p>
                </div>
            </div>

            <!-- Timeline Item 2 -->
            <div class="relative pl-8 sm:pl-10">
                <div class="absolute -left-[17px] top-1.5 w-8 h-8 rounded-full bg-pastel-blush border-2 border-rose-400 flex items-center justify-center text-rose-700 text-xs shadow-sm">
                    <i class="fa-solid fa-book-open"></i>
                </div>
                <div class="glass-card p-6 rounded-2xl border border-pink-100 shadow-sm">
                    <span class="text-xs font-bold text-rose-700 bg-pink-100 px-2.5 py-0.5 rounded-full">9:00 AM • Storytelling & Literature</span>
                    <h3 class="font-serif text-lg font-bold text-pastel-dark mt-2">Bringing Words to Life</h3>
                    <p class="text-xs sm:text-sm text-pastel-muted mt-1 leading-relaxed">
                        Explaining classic poetry and literature with so much emotion and eloquence that everyone listens in awe.
                    </p>
                </div>
            </div>

            <!-- Timeline Item 3 -->
            <div class="relative pl-8 sm:pl-10">
                <div class="absolute -left-[17px] top-1.5 w-8 h-8 rounded-full bg-pastel-lavender border-2 border-purple-400 flex items-center justify-center text-purple-700 text-xs shadow-sm">
                    <i class="fa-solid fa-pen-nib"></i>
                </div>
                <div class="glass-card p-6 rounded-2xl border border-purple-100 shadow-sm">
                    <span class="text-xs font-bold text-purple-700 bg-purple-100 px-2.5 py-0.5 rounded-full">10:00 AM • Grammar & Patience</span>
                    <h3 class="font-serif text-lg font-bold text-pastel-dark mt-2">Gentle Guidance</h3>
                    <p class="text-xs sm:text-sm text-pastel-muted mt-1 leading-relaxed">
                        Patiently clearing every student's doubts and correcting syntax errors with encouragement rather than criticism.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- SECTION 5: 3D VOCABULARY FLASHCARDS -->
    <section id="vocab" class="py-20 px-4 sm:px-6 max-w-6xl mx-auto z-10 relative">
        <div class="text-center mb-12">
            <span class="text-xs uppercase tracking-widest text-pink-500 font-bold">Interactive 3D Cards</span>
            <h2 class="font-serif text-3xl sm:text-4xl font-bold text-pastel-dark mt-1">Vocabulary of Inspiration</h2>
            <p class="text-xs sm:text-sm text-pastel-muted mt-2">Tap any card to flip it in 3D and reveal a hidden note!</p>
            <div class="w-16 h-1 bg-pastel-pink mx-auto mt-3 rounded-full"></div>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
            <!-- Flashcard 1 -->
            <div class="h-64 perspective-1000 cursor-pointer" onclick="flip3DCard(this)">
                <div class="relative w-full h-full transform-style-3d glass-card rounded-2xl p-6 border border-pink-200 shadow-sm hover:shadow-md transition-shadow">
                    <!-- Front -->
                    <div class="absolute inset-0 backface-hidden p-6 flex flex-col justify-between items-center text-center bg-white rounded-2xl">
                        <div class="w-12 h-12 rounded-full bg-pastel-blush flex items-center justify-center text-rose-500 text-xl font-bold"><i class="fa-solid fa-feather"></i></div>
                        <div>
                            <h3 class="font-serif text-2xl text-pastel-dark font-bold mb-1">Eloquence</h3>
                            <p class="text-xs text-pastel-muted italic">/ˈel.ə.kwəns/</p>
                            <p class="text-xs text-pastel-muted mt-2">Fluent or persuasive speaking or writing.</p>
                        </div>
                        <span class="text-xs text-pink-500 font-semibold">Click to flip 🔄</span>
                    </div>
                    <!-- Back -->
                    <div class="absolute inset-0 backface-hidden rotate-y-180 p-6 flex flex-col justify-center items-center text-center bg-pastel-blush rounded-2xl text-pastel-dark">
                        <p class="text-sm font-medium leading-relaxed">"Your eloquence in every lecture makes English feel like pure poetry."</p>
                    </div>
                </div>
            </div>

            <!-- Flashcard 2 -->
            <div class="h-64 perspective-1000 cursor-pointer" onclick="flip3DCard(this)">
                <div class="relative w-full h-full transform-style-3d glass-card rounded-2xl p-6 border border-purple-200 shadow-sm hover:shadow-md transition-shadow">
                    <!-- Front -->
                    <div class="absolute inset-0 backface-hidden p-6 flex flex-col justify-between items-center text-center bg-white rounded-2xl">
                        <div class="w-12 h-12 rounded-full bg-pastel-lavender flex items-center justify-center text-purple-600 text-xl font-bold"><i class="fa-solid fa-gem"></i></div>
                        <div>
                            <h3 class="font-serif text-2xl text-pastel-dark font-bold mb-1">Ethereal</h3>
                            <p class="text-xs text-pastel-muted italic">/ɪˈθɪə.ri.əl/</p>
                            <p class="text-xs text-pastel-muted mt-2">Extremely delicate, light, and heavenly.</p>
                        </div>
                        <span class="text-xs text-purple-500 font-semibold">Click to flip 🔄</span>
                    </div>
                    <!-- Back -->
                    <div class="absolute inset-0 backface-hidden rotate-y-180 p-6 flex flex-col justify-center items-center text-center bg-pastel-lavender rounded-2xl text-pastel-dark">
                        <p class="text-sm font-medium leading-relaxed">"You bring an ethereal calm and grace to our everyday school routine."</p>
                    </div>
                </div>
            </div>

            <!-- Flashcard 3 -->
            <div class="h-64 perspective-1000 cursor-pointer" onclick="flip3DCard(this)">
                <div class="relative w-full h-full transform-style-3d glass-card rounded-2xl p-6 border border-emerald-200 shadow-sm hover:shadow-md transition-shadow">
                    <!-- Front -->
                    <div class="absolute inset-0 backface-hidden p-6 flex flex-col justify-between items-center text-center bg-white rounded-2xl">
                        <div class="w-12 h-12 rounded-full bg-pastel-mint flex items-center justify-center text-emerald-600 text-xl font-bold"><i class="fa-solid fa-seedling"></i></div>
                        <div>
                            <h3 class="font-serif text-2xl text-pastel-dark font-bold mb-1">Resilience</h3>
                            <p class="text-xs text-pastel-muted italic">/rɪˈzɪl.jəns/</p>
                            <p class="text-xs text-pastel-muted mt-2">The capacity to withstand and recover quickly.</p>
                        </div>
                        <span class="text-xs text-emerald-600 font-semibold">Click to flip 🔄</span>
                    </div>
                    <!-- Back -->
                    <div class="absolute inset-0 backface-hidden rotate-y-180 p-6 flex flex-col justify-center items-center text-center bg-pastel-mint rounded-2xl text-pastel-dark">
                        <p class="text-sm font-medium leading-relaxed">"Thank you for teaching us resilience both in studies and in life!"</p>
                    </div>
                </div>
            </div>

            <!-- Flashcard 4 -->
            <div class="h-64 perspective-1000 cursor-pointer" onclick="flip3DCard(this)">
                <div class="relative w-full h-full transform-style-3d glass-card rounded-2xl p-6 border border-amber-200 shadow-sm hover:shadow-md transition-shadow">
                    <!-- Front -->
                    <div class="absolute inset-0 backface-hidden p-6 flex flex-col justify-between items-center text-center bg-white rounded-2xl">
                        <div class="w-12 h-12 rounded-full bg-amber-50 flex items-center justify-center text-amber-500 text-xl font-bold"><i class="fa-solid fa-sun"></i></div>
                        <div>
                            <h3 class="font-serif text-2xl text-pastel-dark font-bold mb-1">Sempiternal</h3>
                            <p class="text-xs text-pastel-muted italic">/ˌsem.pɪˈtɜː.nəl/</p>
                            <p class="text-xs text-pastel-muted mt-2">Everlasting and eternal in time.</p>
                        </div>
                        <span class="text-xs text-amber-600 font-semibold">Click to flip 🔄</span>
                    </div>
                    <!-- Back -->
                    <div class="absolute inset-0 backface-hidden rotate-y-180 p-6 flex flex-col justify-center items-center text-center bg-amber-100 rounded-2xl text-pastel-dark">
                        <p class="text-sm font-medium leading-relaxed">"Wishing you sempiternal happiness, good health, and peace on your birthday!"</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- SECTION 6: INTERACTIVE GRATITUDE JAR -->
    <section id="jar" class="py-20 px-4 sm:px-6 max-w-3xl mx-auto z-10 relative">
        <div class="glass-card p-8 sm:p-12 rounded-3xl border border-pink-200/80 text-center shadow-lg bg-gradient-to-b from-white/90 to-pink-50/30">
            <div class="w-16 h-16 bg-pastel-blush text-rose-500 rounded-full flex items-center justify-center mx-auto mb-4 text-2xl shadow-sm">
                <i class="fa-solid fa-jar"></i>
            </div>
            <h2 class="font-serif text-3xl font-bold text-pastel-dark mb-2">The Interactive Gratitude Jar</h2>
            <p class="text-xs sm:text-sm text-pastel-muted mb-6">Click the jar button to draw glowing notes of gratitude!</p>

            <div id="jar-box" class="min-h-[100px] p-6 bg-white rounded-2xl border border-pink-100 shadow-inner flex items-center justify-center mb-6 transition-all duration-300">
                <p id="jar-text" class="font-serif italic text-base sm:text-lg text-pastel-rose font-medium">"Click below to draw a blessing note..."</p>
            </div>

            <button onclick="drawJarNote()" class="px-6 py-3 bg-gradient-to-r from-pink-400 to-rose-400 hover:from-pink-500 hover:to-rose-500 text-white font-semibold rounded-2xl shadow-md hover:shadow-lg transition-all text-sm inline-flex items-center gap-2">
                <i class="fa-solid fa-clover"></i> Draw Gratitude Note
            </button>
        </div>
    </section>

    <!-- SECTION 7: STUDENT WISH WALL -->
    <section id="wishes" class="py-20 px-4 sm:px-6 max-w-6xl mx-auto z-10 relative">
        <div class="text-center mb-12">
            <span class="text-xs uppercase tracking-widest text-pink-500 font-bold">Pastel Sticky Notes</span>
            <h2 class="font-serif text-3xl sm:text-4xl font-bold text-pastel-dark mt-1">Student Wish Wall</h2>
            <div class="w-16 h-1 bg-pastel-pink mx-auto mt-3 rounded-full"></div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <!-- Sticky 1 -->
            <div class="bg-amber-50/90 p-6 rounded-2xl shadow-sm border border-amber-200/80 transform -rotate-1 hover:rotate-0 transition-transform">
                <div class="flex items-center justify-between mb-3">
                    <span class="text-xs font-bold text-amber-800 bg-amber-200/60 px-2.5 py-0.5 rounded-full">💛 Classroom Vibes</span>
                    <i class="fa-solid fa-thumbtack text-amber-400"></i>
                </div>
                <p class="font-serif text-pastel-dark italic text-sm leading-relaxed mb-4">
                    "Happy Birthday ma'am! Thank you for turning every English lecture into a peaceful, creative journey."
                </p>
                <span class="text-xs text-amber-800 font-semibold">— Student Note</span>
            </div>

            <!-- Sticky 2 -->
            <div class="bg-pink-50/90 p-6 rounded-2xl shadow-sm border border-pink-200/80 transform rotate-1 hover:rotate-0 transition-transform">
                <div class="flex items-center justify-between mb-3">
                    <span class="text-xs font-bold text-rose-800 bg-pink-200/60 px-2.5 py-0.5 rounded-full">🌸 Best Wishes</span>
                    <i class="fa-solid fa-thumbtack text-pink-400"></i>
                </div>
                <p class="font-serif text-pastel-dark italic text-sm leading-relaxed mb-4">
                    "May your year ahead be as sweet, cheerful, and inspiring as your teaching!"
                </p>
                <span class="text-xs text-rose-800 font-semibold">— English Club</span>
            </div>

            <!-- Sticky 3 -->
            <div class="bg-purple-50/90 p-6 rounded-2xl shadow-sm border border-purple-200/80 transform -rotate-1 hover:rotate-0 transition-transform">
                <div class="flex items-center justify-between mb-3">
                    <span class="text-xs font-bold text-purple-800 bg-purple-200/60 px-2.5 py-0.5 rounded-full">✨ Mentorship</span>
                    <i class="fa-solid fa-thumbtack text-purple-400"></i>
                </div>
                <p class="font-serif text-pastel-dark italic text-sm leading-relaxed mb-4">
                    "To the teacher who always saw potential in us even when we doubted ourselves. Have the happiest birthday!"
                </p>
                <span class="text-xs text-purple-800 font-semibold">— Grateful Heart</span>
            </div>
        </div>
    </section>

    <!-- SECTION 8: INTERACTIVE TRIVIA QUIZ -->
    <section id="quiz" class="py-20 px-4 sm:px-6 max-w-3xl mx-auto z-10 relative">
        <div class="glass-card p-8 sm:p-10 rounded-3xl border border-purple-200/80 shadow-lg">
            <div class="text-center mb-8">
                <span class="text-xs uppercase tracking-widest text-purple-500 font-bold">Fun Activity</span>
                <h2 class="font-serif text-3xl font-bold text-pastel-dark mt-1">Teacher Special Trivia</h2>
            </div>

            <div class="space-y-6">
                <!-- Q1 -->
                <div class="bg-white/80 p-5 rounded-2xl border border-pink-100">
                    <p class="font-semibold text-pastel-dark text-xs sm:text-sm mb-3">1. What makes our English teacher's class unique?</p>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 text-xs">
                        <button onclick="checkQuiz(this, true)" class="p-3 text-left rounded-xl bg-pastel-cream hover:bg-pastel-blush transition-colors border border-pink-100">A) Her patience and inspiring words ✨</button>
                        <button onclick="checkQuiz(this, false)" class="p-3 text-left rounded-xl bg-pastel-cream hover:bg-pastel-blush transition-colors border border-pink-100">B) Strict surprise tests only</button>
                    </div>
                </div>

                <!-- Q2 -->
                <div class="bg-white/80 p-5 rounded-2xl border border-pink-100">
                    <p class="font-semibold text-pastel-dark text-xs sm:text-sm mb-3">2. Which month holds this special birthday celebration?</p>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 text-xs">
                        <button onclick="checkQuiz(this, false)" class="p-3 text-left rounded-xl bg-pastel-cream hover:bg-pastel-blush transition-colors border border-pink-100">A) December</button>
                        <button onclick="checkQuiz(this, true)" class="p-3 text-left rounded-xl bg-pastel-cream hover:bg-pastel-blush transition-colors border border-pink-100">B) August 🎈</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- SECTION 9: VIRTUAL GIFT UNBOXING -->
    <section id="unboxing" class="py-20 px-4 sm:px-6 max-w-2xl mx-auto text-center z-10 relative">
        <div class="glass-card p-8 sm:p-12 rounded-3xl border border-pink-200 shadow-xl bg-gradient-to-b from-white to-pink-50/50">
            <span class="text-xs uppercase tracking-widest text-pink-500 font-bold">Grand Finale</span>
            <h2 class="font-serif text-3xl font-bold text-pastel-dark mt-1 mb-6">Virtual Gift Box</h2>

            <div id="gift-box" class="cursor-pointer my-6 inline-block transform hover:scale-105 transition-transform" onclick="openGiftBox()">
                <div class="w-32 h-32 bg-gradient-to-tr from-pink-300 to-purple-300 rounded-2xl shadow-lg border-2 border-white flex items-center justify-center relative mx-auto">
                    <!-- Ribbon -->
                    <div class="absolute inset-x-0 h-6 bg-rose-400/80 top-13"></div>
                    <div class="absolute inset-y-0 w-6 bg-rose-400/80 left-13"></div>
                    <i class="fa-solid fa-gift text-5xl text-white z-10 drop-shadow"></i>
                </div>
                <p class="text-xs text-pink-600 font-semibold mt-4">Tap to unbox your final message 🎁</p>
            </div>

            <div id="gift-message" class="hidden mt-6 p-6 bg-white rounded-2xl border border-pink-200 text-pastel-rose font-serif text-lg leading-relaxed shadow-inner">
                🌸 "May your birthday be as warm, bright, and beautiful as the wisdom you share with us every day! Thank you for being the absolute best teacher!" 🌸
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="py-10 text-center border-t border-pink-100 glass-card mt-12 relative z-10">
        <p class="font-script text-2xl sm:text-3xl text-pastel-rose font-bold mb-1">Happy Birthday Once Again!</p>
        <p class="text-xs text-pastel-muted">Crafted with respect, admiration, and gratitude for our favorite English Teacher.</p>
    </footer>

    <!-- JAVASCRIPT LOGIC & THREE.JS ENGINE -->
    <script>
        /* --- 1. THREE.JS 3D BACKGROUND ENGINE --- */
        let scene, camera, renderer, bookMeshGroup, particlesMesh;

        function init3D() {
            const canvas = document.getElementById('three-canvas');
            scene = new THREE.Scene();

            // Camera setup
            camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 0.1, 1000);
            camera.position.z = 15;

            // Renderer setup
            renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true, antialias: true });
            renderer.setSize(window.innerWidth, window.innerHeight);
            renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

            // Ambient Light & Directional Light
            const ambientLight = new THREE.AmbientLight(0xffffff, 0.8);
            scene.add(ambientLight);

            const dirLight = new THREE.DirectionalLight(0xfbcfe8, 1);
            dirLight.position.set(5, 10, 7);
            scene.add(dirLight);

            // Group for 3D Books/Geometries
            bookMeshGroup = new THREE.Group();

            // Create Floating 3D Book Geometries
            const bookGeo = new THREE.BoxGeometry(1.5, 2, 0.4);
            const bookMaterials = [
                new THREE.MeshStandardMaterial({ color: 0xfbcfe8 }), // Pink
                new THREE.MeshStandardMaterial({ color: 0xf3e8ff }), // Lavender
                new THREE.MeshStandardMaterial({ color: 0xe6f4ea }), // Mint
                new THREE.MeshStandardMaterial({ color: 0xffe8d6 }), // Peach
            ];

            for (let i = 0; i < 18; i++) {
                const mat = bookMaterials[i % bookMaterials.length];
                const book = new THREE.Mesh(bookGeo, mat);

                book.position.x = (Math.random() - 0.5) * 25;
                book.position.y = (Math.random() - 0.5) * 25;
                book.position.z = (Math.random() - 0.5) * 15;

                book.rotation.x = Math.random() * Math.PI;
                book.rotation.y = Math.random() * Math.PI;

                bookMeshGroup.add(book);
            }
            scene.add(bookMeshGroup);

            // Floating Golden Particles
            const particleGeo = new THREE.BufferGeometry();
            const particleCount = 120;
            const posArray = new Float32Array(particleCount * 3);

            for (let i = 0; i < particleCount * 3; i++) {
                posArray[i] = (Math.random() - 0.5) * 30;
            }

            particleGeo.setAttribute('position', new THREE.BufferAttribute(posArray, 3));
            const particleMat = new THREE.PointsMaterial({
                size: 0.12,
                color: 0xd97706,
                transparent: true,
                opacity: 0.6
            });

            particlesMesh = new THREE.Points(particleGeo, particleMat);
            scene.add(particlesMesh);

            // Mouse Move Parallax Listener
            window.addEventListener('mousemove', onMouseMove);
            window.addEventListener('resize', onWindowResize);

            // Start Animation Loop
            animate3D();
        }

        let mouseX = 0, mouseY = 0;
        function onMouseMove(event) {
            mouseX = (event.clientX / window.innerWidth - 0.5) * 2;
            mouseY = (event.clientY / window.innerHeight - 0.5) * 2;
        }

        function onWindowResize() {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        }

        function animate3D() {
            requestAnimationFrame(animate3D);

            // Rotate book elements slowly
            if (bookMeshGroup) {
                bookMeshGroup.children.forEach((child, index) => {
                    child.rotation.x += 0.003 + index * 0.0001;
                    child.rotation.y += 0.004 + index * 0.0001;
                });
            }

            // Rotate particles
            if (particlesMesh) {
                particlesMesh.rotation.y += 0.001;
            }

            // Subtle Camera movement based on mouse
            camera.position.x += (mouseX * 2 - camera.position.x) * 0.03;
            camera.position.y += (-mouseY * 2 - camera.position.y) * 0.03;
            camera.lookAt(scene.position);

            renderer.render(scene, camera);
        }

        // Initialize Three.js on Window Load
        window.onload = function() {
            init3D();
        };

        /* --- 2. INTERACTIVE UI FUNCTIONS --- */

        // Candle Blow Function
        let isCandleLit = true;
        function blowCandle() {
            const flame = document.getElementById('cake-flame');
            const msg = document.getElementById('candle-message');

            if (isCandleLit) {
                flame.style.display = 'none';
                msg.innerText = "✨ Woohoo! Candle blown! May all your wishes come true! 🎉";
                triggerEpicConfetti();
                isCandleLit = false;
            } else {
                flame.style.display = 'block';
                msg.innerText = "🔥 The candle is lit! Make a birthday wish & tap the flame!";
                isCandleLit = true;
            }
        }

        // 3D Card Flip
        function flip3DCard(card) {
            const innerCard = card.querySelector('.transform-style-3d');
            innerCard.classList.toggle('flipped');
        }

        // Gratitude Jar Generator
        const jarNotes = [
            "🌸 May your day be as inspiring as your lectures!",
            "☕ Wishing you peaceful mornings with a perfect cup of tea and a good book.",
            "📚 Thank you for making literature feel magical and alive.",
            "✨ Your gentle patience leaves a lasting footprint on every student's heart.",
            "🎁 Wishing you endless blessings, health, and peace this year!"
        ];

        function drawJarNote() {
            const jarText = document.getElementById('jar-text');
            const random = jarNotes[Math.floor(Math.random() * jarNotes.length)];
            jarText.style.opacity = '0';
            setTimeout(() => {
                jarText.innerText = `"${random}"`;
                jarText.style.opacity = '1';
            }, 200);
            triggerEpicConfetti();
        }

        // Quiz Check
        function checkQuiz(btn, isCorrect) {
            if (isCorrect) {
                btn.classList.remove('bg-pastel-cream');
                btn.classList.add('bg-emerald-100', 'text-emerald-800', 'font-bold');
                triggerEpicConfetti();
            } else {
                btn.classList.remove('bg-pastel-cream');
                btn.classList.add('bg-rose-100', 'text-rose-800');
            }
        }

        // Gift Box Unboxing
        function openGiftBox() {
            const giftMsg = document.getElementById('gift-message');
            giftMsg.classList.toggle('hidden');
            triggerEpicConfetti();
        }

        // Audio Toggle Placeholder
        let isPlaying = false;
        function toggleAudio() {
            const icon = document.getElementById('audio-icon');
            isPlaying = !isPlaying;
            if (isPlaying) {
                icon.classList.remove('fa-music');
                icon.classList.add('fa-volume-high');
            } else {
                icon.classList.remove('fa-volume-high');
                icon.classList.add('fa-music');
            }
        }

        // Canvas Confetti
        function triggerEpicConfetti() {
            if (typeof confetti === 'function') {
                confetti({
                    particleCount: 80,
                    spread: 80,
                    origin: { y: 0.6 },
                    colors: ['#FBCFE8', '#F3E8FF', '#E6F4EA', '#D97706', '#E11D48']
                });
            }
        }
    </script>
</body>
</html>

