const searchInput = document.getElementById('google-search-input');
const urlInput = document.getElementById('chrome-url-input');
const voiceBtn = document.getElementById('voice-btn');
const tabGoogle = document.getElementById('tab-google');
const tabLuizabeth = document.getElementById('tab-luizabeth');
const googleView = document.getElementById('google-view');
const portfolioView = document.getElementById('portfolio-view');

// --- Lista de flores para alternar ---
const flowerImages = [
    '+jfhjs-removebg-preview.png',
    '88-removebg-preview.png',
    'hghg-removebg-preview.png',
    'hh-removebg-preview.png',
    'yyy-removebg-preview.png'
];

// Lógica para alternar las imágenes de las flores cada 6 segundos de forma suave
function initFlowerSlideshow(containerId, startIdx) {
    let currentIdx = startIdx;
    const container = document.getElementById(containerId);
    if (!container) return;
    const img1 = container.querySelector('.flower-img-1');
    const img2 = container.querySelector('.flower-img-2');
    let isImg1Active = true;

    img1.src = flowerImages[currentIdx];

    setInterval(() => {
        currentIdx = (currentIdx + 1) % flowerImages.length;

        if (isImg1Active) {
            img2.src = flowerImages[currentIdx];
            img2.classList.add('active');
            img1.classList.remove('active');
        } else {
            img1.src = flowerImages[currentIdx];
            img1.classList.add('active');
            img2.classList.remove('active');
        }

        isImg1Active = !isImg1Active;
    }, 6000);
}

// Iniciar las transiciones de las flores
initFlowerSlideshow('flower-left-container', 0); // Empieza en Img 1
initFlowerSlideshow('flower-right-container', 1); // Empieza en Img 2

// --- Sintetizador de sonido de teclado mecánico (Web Audio API) ---
let audioCtx = null;

function playKeyboardSound() {
    try {
        if (!audioCtx) {
            audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        }
        if (audioCtx.state === 'suspended') {
            audioCtx.resume();
        }

        const now = audioCtx.currentTime;

        const bufferSize = audioCtx.sampleRate * 0.015;
        const buffer = audioCtx.createBuffer(1, bufferSize, audioCtx.sampleRate);
        const output = buffer.getChannelData(0);
        for (let i = 0; i < bufferSize; i++) {
            output[i] = Math.random() * 2 - 1;
        }

        const noiseSource = audioCtx.createBufferSource();
        noiseSource.buffer = buffer;

        const bandpass = audioCtx.createBiquadFilter();
        bandpass.type = 'bandpass';
        bandpass.frequency.value = 2200 + Math.random() * 600;
        bandpass.Q.value = 2.5;

        const noiseGain = audioCtx.createGain();
        noiseGain.gain.setValueAtTime(0.12, now);
        noiseGain.gain.exponentialRampToValueAtTime(0.001, now + 0.015);

        noiseSource.connect(bandpass);
        bandpass.connect(noiseGain);
        noiseGain.connect(audioCtx.destination);

        noiseSource.start(now);

        const osc = audioCtx.createOscillator();
        const oscGain = audioCtx.createGain();

        osc.type = 'sine';
        osc.frequency.setValueAtTime(140 + Math.random() * 30, now);
        osc.frequency.exponentialRampToValueAtTime(30, now + 0.02);

        oscGain.gain.setValueAtTime(0.18, now);
        oscGain.gain.exponentialRampToValueAtTime(0.001, now + 0.02);

        osc.connect(oscGain);
        oscGain.connect(audioCtx.destination);

        osc.start(now);
        osc.stop(now + 0.025);
    } catch (e) {
        // Silenciar en caso de restricción de autoplay
    }
}

// Emitir sonido al teclear
[searchInput, urlInput].forEach(input => {
    if (input) {
        input.addEventListener('keydown', (e) => {
            if (e.key !== 'Enter' && !e.ctrlKey && !e.altKey) {
                playKeyboardSound();
            }
        });
    }
});

function switchTab(view) {
    if (view === 'google') {
        tabGoogle.className = "tab-item tab-active";
        tabLuizabeth.className = "tab-item tab-inactive";
        googleView.style.display = "flex";
        portfolioView.style.display = "none";
        urlInput.value = "google.com";
    } else {
        tabLuizabeth.className = "tab-item tab-active";
        tabGoogle.className = "tab-item tab-inactive";
        googleView.style.display = "none";
        portfolioView.style.display = "block";
        urlInput.value = "luizabeth.html";
    }
}

function performSearch(query) {
    const term = query.toLowerCase().trim();
    const toast = document.getElementById('search-toast');
    document.getElementById('toast-term').textContent = query;

    toast.classList.remove('hidden');

    setTimeout(() => {
        toast.classList.add('hidden');

        if (term.includes("luizabeth")) {
            tabLuizabeth.classList.remove('hidden');
            switchTab('luizabeth');
        } else {
            window.open(`https://www.google.com/search?q=${encodeURIComponent(query)}`, '_blank');
        }
    }, 1200);
}

if (searchInput) {
    searchInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter' && searchInput.value) {
            performSearch(searchInput.value);
        }
    });
}

// Búsqueda por voz
const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

if (SpeechRecognition && voiceBtn) {
    const recognition = new SpeechRecognition();
    recognition.lang = 'es-VE';
    recognition.continuous = false;
    recognition.interimResults = false;
    recognition.maxAlternatives = 1;

    let listening = false;

    voiceBtn.title = "Buscar por voz";
    voiceBtn.style.cursor = "pointer";

    voiceBtn.addEventListener('click', () => {
        if (listening) return;
        try {
            recognition.start();
        } catch (e) {
            // Ignorar si ya está iniciado
        }
    });

    recognition.onstart = () => {
        listening = true;
        voiceBtn.style.backgroundColor = "#ff000033";
        voiceBtn.title = "Escuchando...";
    };

    recognition.onresult = (e) => {
        const result = e.results[0][0].transcript;
        searchInput.value = result;
        performSearch(result);
    };

    recognition.onerror = (e) => {
        console.warn("Error de reconocimiento de voz:", e.error);
        if (e.error === 'not-allowed') {
            alert("Permiso de micrófono denegado. Actívalo en la configuración del navegador.");
        }
    };

    recognition.onend = () => {
        listening = false;
        voiceBtn.style.backgroundColor = "transparent";
        voiceBtn.title = "Buscar por voz";
    };
} else if (voiceBtn) {
    voiceBtn.title = "Tu navegador no soporta búsqueda por voz";
    voiceBtn.style.opacity = "0.4";
    voiceBtn.style.cursor = "not-allowed";

    voiceBtn.addEventListener('click', () => {
        alert("Tu navegador no soporta búsqueda por voz.\nUsa Chrome, Edge o Safari para esta función.");
    });
}
