<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Timer Belajar & Pomodoro</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom styles for smoother animations and hiding scrollbar */
        body {
            -webkit-tap-highlight-color: transparent;
        }
        input[type="number"]::-webkit-inner-spin-button,
        input[type="number"]::-webkit-outer-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }
        .glass-panel {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
        }
        .btn-press:active {
            transform: scale(0.95);
        }
        .progress-transition {
            transition: width 1s linear;
        }
    </style>
</head>
<body class="min-h-screen bg-gradient-to-br from-slate-900 via-indigo-950 to-slate-900 flex items-center justify-center p-4 text-white font-sans antialiased overflow-hidden">

    <!-- Ambient background glows -->
    <div class="fixed top-[-10%] left-[-10%] w-[40%] h-[40%] rounded-full bg-purple-600/30 blur-[120px] pointer-events-none"></div>
    <div class="fixed bottom-[-10%] right-[-10%] w-[40%] h-[40%] rounded-full bg-blue-600/20 blur-[120px] pointer-events-none"></div>

    <!-- Main Application Card -->
    <main class="glass-panel w-full max-w-md rounded-[2.5rem] p-8 relative z-10 flex flex-col items-center transition-all duration-500">
        
        <!-- Mode Tabs -->
        <div class="w-full bg-black/20 p-1.5 rounded-full flex gap-1 mb-8">
            <button id="tab-pomodoro" class="flex-1 py-2 rounded-full text-sm font-medium transition-all duration-300 bg-white/20 text-white shadow-sm" onclick="app.setMode('pomodoro')">
                🍅 Pomodoro
            </button>
            <button id="tab-timer" class="flex-1 py-2 rounded-full text-sm font-medium transition-all duration-300 text-white/50 hover:text-white" onclick="app.setMode('timer')">
                ⏱️ Custom Timer
            </button>
        </div>

        <!-- Pomodoro Indicator (Only visible in Pomodoro Mode) -->
        <div id="pomodoro-indicator" class="flex flex-col items-center mb-4 h-12 transition-all">
            <span id="phase-badge" class="px-3 py-1 rounded-full text-xs font-semibold bg-indigo-500/30 text-indigo-200 border border-indigo-500/30 mb-2">
                Fokus
            </span>
            <div class="flex gap-1.5" id="session-dots">
                <!-- Dots populated by JS -->
            </div>
        </div>

        <!-- Custom Timer Input (Only visible in Timer Mode) -->
        <div id="custom-timer-input" class="hidden flex-col items-center mb-4 h-12 justify-center w-full">
            <div class="flex items-center gap-2 bg-black/20 px-4 py-2 rounded-2xl border border-white/10">
                <input type="number" id="custom-minutes" value="10" min="1" max="999" class="bg-transparent text-white w-12 text-center text-lg outline-none font-semibold">
                <span class="text-white/60 text-sm">Menit</span>
                <button onclick="app.applyCustomTimer()" class="ml-2 bg-white/10 hover:bg-white/20 p-1.5 rounded-xl transition">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                </button>
            </div>
        </div>

        <!-- Time Display -->
        <div class="relative w-full flex justify-center items-center my-6 group">
            <h1 id="time-display" class="text-[5.5rem] leading-none font-bold tracking-tighter text-transparent bg-clip-text bg-gradient-to-b from-white to-white/70 tabular-nums">
                25:00
            </h1>
        </div>

        <!-- Progress Bar -->
        <div class="w-full h-2 bg-black/30 rounded-full mb-10 overflow-hidden relative border border-white/5">
            <div id="progress-bar" class="h-full bg-gradient-to-r from-indigo-400 to-purple-400 w-full progress-transition rounded-full shadow-[0_0_10px_rgba(167,139,250,0.5)]"></div>
        </div>

        <!-- Controls -->
        <div class="flex items-center justify-center gap-6 w-full">
            <!-- Reset Button -->
            <button onclick="app.resetTimer()" class="btn-press w-14 h-14 flex items-center justify-center rounded-2xl bg-white/5 hover:bg-white/10 border border-white/10 transition-colors text-white/70 hover:text-white">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"></path></svg>
            </button>

            <!-- Play/Pause Button -->
            <button id="play-pause-btn" onclick="app.togglePlay()" class="btn-press w-20 h-20 flex items-center justify-center rounded-[2rem] bg-gradient-to-tr from-indigo-600 to-purple-500 shadow-lg shadow-indigo-500/30 hover:shadow-indigo-500/50 hover:scale-105 transition-all text-white border border-white/20">
                <svg id="play-icon" class="w-8 h-8 ml-1" fill="currentColor" viewBox="0 0 24 24"><path d="M8 5v14l11-7z"></path></svg>
                <svg id="pause-icon" class="w-8 h-8 hidden" fill="currentColor" viewBox="0 0 24 24"><path d="M6 19h4V5H6v14zm8-14v14h4V5h-4z"></path></svg>
            </button>
        </div>
    </main>

    <script>
        // Web Audio API untuk Notifikasi Suara (tanpa aset eksternal)
        const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        function playAlertSound() {
            if (audioCtx.state === 'suspended') audioCtx.resume();
            
            const playTone = (freq, type, duration, startTime) => {
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = type;
                osc.frequency.setValueAtTime(freq, audioCtx.currentTime + startTime);
                
                // Mengubah envelope gain untuk suara "beep" yang stabil dan tidak memudar (bukan efek ping)
                gain.gain.setValueAtTime(0, audioCtx.currentTime + startTime);
                gain.gain.linearRampToValueAtTime(0.5, audioCtx.currentTime + startTime + 0.05); // Attack cepat
                gain.gain.setValueAtTime(0.5, audioCtx.currentTime + startTime + duration - 0.05); // Tahan volume (sustain)
                gain.gain.linearRampToValueAtTime(0.001, audioCtx.currentTime + startTime + duration); // Release cepat
                
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start(audioCtx.currentTime + startTime);
                osc.stop(audioCtx.currentTime + startTime + duration);
            };

            // Memainkan suara "nit, nit, nit" berulang selama ~5 detik
            // 5 perulangan, setiap bunyi 0.5 detik, jeda 0.5 detik
            for (let i = 0; i < 8; i++) {
                playTone(800, 'sine', 0.1, i * 0.2); 
            }
        }

        // --- Core Application Logic ---
        const POMODORO_FOCUS = 25 * 60;
        const POMODORO_SHORT_BREAK = 5 * 60;
        const POMODORO_LONG_BREAK = 15 * 60;

        const app = {
            state: {
                mode: 'pomodoro', // 'pomodoro' | 'timer'
                status: 'idle',   // 'idle' | 'running' | 'paused'
                timeLeft: POMODORO_FOCUS,
                totalTime: POMODORO_FOCUS,
                pomodoroPhase: 'focus', // 'focus' | 'shortBreak' | 'longBreak'
                sessionCount: 1, // 1 to 4
                targetEndTime: null
            },
            interval: null,

            // DOM Elements
            els: {
                timeDisplay: document.getElementById('time-display'),
                progressBar: document.getElementById('progress-bar'),
                playIcon: document.getElementById('play-icon'),
                pauseIcon: document.getElementById('pause-icon'),
                tabPomodoro: document.getElementById('tab-pomodoro'),
                tabTimer: document.getElementById('tab-timer'),
                pomodoroIndicator: document.getElementById('pomodoro-indicator'),
                customTimerInput: document.getElementById('custom-timer-input'),
                sessionDots: document.getElementById('session-dots'),
                phaseBadge: document.getElementById('phase-badge'),
                customMinutes: document.getElementById('custom-minutes')
            },

            init() {
                this.loadState();
                this.updateUI();
                
                // Jika aplikasi ditinggal (reload/close tab) saat jalan, hitung waktu terlewat
                if (this.state.status === 'running' && this.state.targetEndTime) {
                    const now = Date.now();
                    if (now < this.state.targetEndTime) {
                        this.state.timeLeft = Math.ceil((this.state.targetEndTime - now) / 1000);
                        this.startTimer(false); // resume tanpa sound init
                    } else {
                        this.handleSessionEnd();
                    }
                }
            },

            loadState() {
                const saved = localStorage.getItem('timerState');
                if (saved) {
                    try {
                        this.state = JSON.parse(saved);
                    } catch (e) {
                        console.error("Gagal load state");
                    }
                }
            },

            saveState() {
                localStorage.setItem('timerState', JSON.stringify(this.state));
            },

            setMode(newMode) {
                if (this.state.mode === newMode) return;
                this.pauseTimer();
                this.state.mode = newMode;
                this.state.status = 'idle';
                
                if (newMode === 'pomodoro') {
                    this.state.pomodoroPhase = 'focus';
                    this.state.sessionCount = 1;
                    this.state.timeLeft = POMODORO_FOCUS;
                    this.state.totalTime = POMODORO_FOCUS;
                } else {
                    this.applyCustomTimer();
                }
                this.updateUI();
                this.saveState();
            },

            applyCustomTimer() {
                let mins = parseInt(this.els.customMinutes.value) || 10;
                if (mins < 1) mins = 1;
                const secs = mins * 60;
                this.pauseTimer();
                this.state.status = 'idle';
                this.state.timeLeft = secs;
                this.state.totalTime = secs;
                this.updateUI();
                this.saveState();
            },

            togglePlay() {
                if (audioCtx.state === 'suspended') audioCtx.resume(); // Unlock audio context di interaksi pertama
                
                if (this.state.status === 'running') {
                    this.pauseTimer();
                } else {
                    this.startTimer();
                }
            },

            startTimer(isNew = true) {
                if (this.state.timeLeft <= 0) this.resetTimer();
                
                this.state.status = 'running';
                if (isNew) {
                    this.state.targetEndTime = Date.now() + (this.state.timeLeft * 1000);
                }
                this.updateUI();
                this.saveState();

                clearInterval(this.interval);
                this.interval = setInterval(() => {
                    this.state.timeLeft = Math.ceil((this.state.targetEndTime - Date.now()) / 1000);
                    
                    if (this.state.timeLeft <= 0) {
                        this.state.timeLeft = 0;
                        this.handleSessionEnd();
                    } else {
                        this.updateUI(true); // Update time & progress only
                        // Hanya save ke localstorage tiap 5 detik agar performa smooth
                        if (this.state.timeLeft % 5 === 0) this.saveState(); 
                    }
                }, 1000);
            },

            pauseTimer() {
                this.state.status = 'paused';
                this.state.targetEndTime = null;
                clearInterval(this.interval);
                this.updateUI();
                this.saveState();
            },

            resetTimer() {
                this.pauseTimer();
                this.state.status = 'idle';
                if (this.state.mode === 'pomodoro') {
                    if (this.state.pomodoroPhase === 'focus') this.state.timeLeft = POMODORO_FOCUS;
                    else if (this.state.pomodoroPhase === 'shortBreak') this.state.timeLeft = POMODORO_SHORT_BREAK;
                    else this.state.timeLeft = POMODORO_LONG_BREAK;
                    this.state.totalTime = this.state.timeLeft;
                } else {
                    this.applyCustomTimer();
                }
                this.updateUI();
                this.saveState();
            },

            handleSessionEnd() {
                this.pauseTimer();
                playAlertSound();

                setTimeout(() => {
                    if (this.state.mode === 'pomodoro') {
                        let msg = "";
                        if (this.state.pomodoroPhase === 'focus') {
                            if (this.state.sessionCount % 4 === 0) {
                                this.state.pomodoroPhase = 'longBreak';
                                this.state.timeLeft = POMODORO_LONG_BREAK;
                                msg = "Selamat! Sesi fokus ke-4 selesai. Waktunya istirahat panjang (15 mnt).";
                            } else {
                                this.state.pomodoroPhase = 'shortBreak';
                                this.state.timeLeft = POMODORO_SHORT_BREAK;
                                msg = `Sesi fokus ke-${this.state.sessionCount} selesai! Waktunya istirahat singkat (5 mnt).`;
                            }
                        } else {
                            // Selesai break, kembali ke focus
                            if (this.state.pomodoroPhase === 'longBreak') {
                                this.state.sessionCount = 1; // Reset counter
                            } else {
                                this.state.sessionCount++;
                            }
                            this.state.pomodoroPhase = 'focus';
                            this.state.timeLeft = POMODORO_FOCUS;
                            msg = "Waktu istirahat selesai. Mari kembali fokus!";
                        }
                        this.state.totalTime = this.state.timeLeft;
                        alert(msg);
                        this.startTimer(); // Auto start phase berikutnya
                    } else {
                        this.state.status = 'idle';
                        alert("Waktu habis!");
                        this.resetTimer();
                    }
                }, 500); // Jeda sedikit agar UI update ke 00:00 sebelum alert
            },

            updateUI(fastUpdate = false) {
                // 1. Update Waktu & Progress Bar (Cepat, dipanggil setiap detik)
                const m = Math.floor(this.state.timeLeft / 60).toString().padStart(2, '0');
                const s = (this.state.timeLeft % 60).toString().padStart(2, '0');
                this.els.timeDisplay.innerText = `${m}:${s}`;
                document.title = `(${m}:${s}) - Timer`;

                const progressPercent = ((this.state.totalTime - this.state.timeLeft) / this.state.totalTime) * 100;
                this.els.progressBar.style.width = `${progressPercent}%`;

                if (fastUpdate) return; // Skip update sisanya jika hanya tick timer

                // 2. Update Tombol & Tab (Lambat, dipanggil saat state ganti)
                if (this.state.status === 'running') {
                    this.els.playIcon.classList.add('hidden');
                    this.els.pauseIcon.classList.remove('hidden');
                } else {
                    this.els.playIcon.classList.remove('hidden');
                    this.els.pauseIcon.classList.add('hidden');
                }

                // Update Style Tabs
                if (this.state.mode === 'pomodoro') {
                    this.els.tabPomodoro.className = "flex-1 py-2 rounded-full text-sm font-medium transition-all duration-300 bg-white/20 text-white shadow-sm";
                    this.els.tabTimer.className = "flex-1 py-2 rounded-full text-sm font-medium transition-all duration-300 text-white/50 hover:text-white";
                    
                    this.els.pomodoroIndicator.classList.remove('hidden');
                    this.els.pomodoroIndicator.classList.add('flex');
                    this.els.customTimerInput.classList.remove('flex');
                    this.els.customTimerInput.classList.add('hidden');

                    this.renderPomodoroDots();
                    
                    // Update Badge Phase
                    if (this.state.pomodoroPhase === 'focus') {
                        this.els.phaseBadge.innerText = `🔥 Fokus - Sesi ${this.state.sessionCount}`;
                        this.els.phaseBadge.className = "px-3 py-1 rounded-full text-xs font-semibold bg-pink-500/30 text-pink-200 border border-pink-500/30 mb-2";
                        this.els.progressBar.className = "h-full bg-gradient-to-r from-pink-500 to-rose-400 w-full progress-transition rounded-full shadow-[0_0_10px_rgba(244,114,182,0.5)]";
                    } else if (this.state.pomodoroPhase === 'shortBreak') {
                        this.els.phaseBadge.innerText = `☕ Istirahat Singkat`;
                        this.els.phaseBadge.className = "px-3 py-1 rounded-full text-xs font-semibold bg-emerald-500/30 text-emerald-200 border border-emerald-500/30 mb-2";
                        this.els.progressBar.className = "h-full bg-gradient-to-r from-emerald-400 to-teal-400 w-full progress-transition rounded-full shadow-[0_0_10px_rgba(52,211,153,0.5)]";
                    } else {
                        this.els.phaseBadge.innerText = `🛌 Istirahat Panjang`;
                        this.els.phaseBadge.className = "px-3 py-1 rounded-full text-xs font-semibold bg-blue-500/30 text-blue-200 border border-blue-500/30 mb-2";
                        this.els.progressBar.className = "h-full bg-gradient-to-r from-blue-400 to-cyan-400 w-full progress-transition rounded-full shadow-[0_0_10px_rgba(96,165,250,0.5)]";
                    }

                } else {
                    this.els.tabPomodoro.className = "flex-1 py-2 rounded-full text-sm font-medium transition-all duration-300 text-white/50 hover:text-white";
                    this.els.tabTimer.className = "flex-1 py-2 rounded-full text-sm font-medium transition-all duration-300 bg-white/20 text-white shadow-sm";
                    
                    this.els.pomodoroIndicator.classList.add('hidden');
                    this.els.pomodoroIndicator.classList.remove('flex');
                    this.els.customTimerInput.classList.add('flex');
                    this.els.customTimerInput.classList.remove('hidden');
                    
                    this.els.progressBar.className = "h-full bg-gradient-to-r from-indigo-400 to-purple-400 w-full progress-transition rounded-full shadow-[0_0_10px_rgba(167,139,250,0.5)]";
                }
            },

            renderPomodoroDots() {
                this.els.sessionDots.innerHTML = '';
                for (let i = 1; i <= 4; i++) {
                    const dot = document.createElement('div');
                    if (i < this.state.sessionCount) {
                        dot.className = "w-2.5 h-2.5 rounded-full bg-white"; // Selesai
                    } else if (i === this.state.sessionCount) {
                        dot.className = "w-2.5 h-2.5 rounded-full bg-white shadow-[0_0_8px_white] animate-pulse"; // Aktif
                    } else {
                        dot.className = "w-2.5 h-2.5 rounded-full bg-white/20"; // Belum
                    }
                    this.els.sessionDots.appendChild(dot);
                }
            }
        };

        // Initialize App
        window.onload = () => app.init();
    </script>
</body>
</html>
