<!DOCTYPE html>
<html lang="th">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ถึงคนที่รักที่สุด 💕</title>

    <!-- ════════════════════════════════════════════════════════════
         💖 FAVICON - โลโก้ที่แสดงในแท็บเบราว์เซอร์
         ════════════════════════════════════════════════════════════
         
         วิธีที่ 1: ใช้ Emoji (กำลังใช้อยู่)
         - เปลี่ยน emoji ใน viewBox ได้เลย (💕, ❤️, 💖, 🌹 เป็นต้น)
         
         วิธีที่ 2: ใช้ไฟล์รูป
         - ดาวน์โหลดรูปหัวใจมาเป็น favicon.png (32x32px)
         - วางไว้โฟลเดอร์เดียวกับ HTML
         - แก้เป็น: <link rel="icon" href="favicon.png" type="image/png">
         
         วิธีที่ 3: สร้างจาก Favicon Generator
         - ไป https://favicon.io
         - สร้างและดาวน์โหลดมา
         ════════════════════════════════════════════════════════════ -->
    <link rel="icon"
        href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='0.9em' font-size='90'>💕</text></svg>">
    <style>
        /* ═══════════════════════════════════════════════════════════════
           FONTS & RESET
           ═══════════════════════════════════════════════════════════════ */
        @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600&family=Sarabun:wght@300;400;500&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Sarabun', sans-serif;
            background: linear-gradient(135deg, #ffdde1 0%, #ee9ca7 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            overflow-x: hidden;
        }

        /* Background Hearts */
        .hearts-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: 1;
        }

        .heart {
            position: absolute;
            bottom: -50px;
            font-size: 30px;
            opacity: 0.5;
            animation: float-up 8s infinite ease-in;
        }

        @keyframes float-up {
            0% {
                bottom: -50px;
                opacity: 0.5;
                transform: translateX(0) rotate(0deg);
            }

            50% {
                opacity: 0.8;
            }

            100% {
                bottom: 110%;
                opacity: 0;
                transform: translateX(100px) rotate(360deg);
            }
        }

        /* Main Card */
        .love-card {
            position: relative;
            z-index: 10;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 30px;
            box-shadow: 0 20px 60px rgba(238, 156, 167, 0.4);
            max-width: 500px;
            width: 100%;
            padding: 40px 30px;
            animation: fadeIn 1s ease;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Music Control */
        .music-control {
            position: absolute;
            top: 20px;
            right: 20px;
            width: 50px;
            height: 50px;
            background: rgba(255, 182, 193, 0.3);
            border-radius: 50%;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            transition: all 0.3s ease;
            z-index: 100;
        }

        .music-control:hover {
            background: rgba(255, 182, 193, 0.5);
            transform: scale(1.1);
        }

        .music-control.playing {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {

            0%,
            100% {
                box-shadow: 0 0 0 0 rgba(255, 182, 193, 0.7);
            }

            50% {
                box-shadow: 0 0 0 10px rgba(255, 182, 193, 0);
            }
        }

        /* Header */
        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .header h1 {
            font-family: 'Kanit', sans-serif;
            font-size: 2rem;
            background: linear-gradient(135deg, #ff6b95 0%, #ee4466 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
            animation: heartbeat 2s infinite;
        }

        @keyframes heartbeat {

            0%,
            100% {
                transform: scale(1);
            }

            10%,
            30% {
                transform: scale(1.05);
            }

            20%,
            40% {
                transform: scale(1);
            }
        }

        .header p {
            color: #888;
            font-size: 0.95rem;
        }

        /* Image Slideshow */
        .slideshow-container {
            position: relative;
            width: 100%;
            height: 300px;
            margin-bottom: 30px;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: opacity 1s ease-in-out;
        }

        .slide.active {
            opacity: 1;
        }

        .slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .slide-caption {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(transparent, rgba(0, 0, 0, 0.6));
            color: white;
            padding: 30px 20px 15px;
            text-align: center;
            font-size: 0.9rem;
        }

        .slide-dots {
            text-align: center;
            margin-top: -20px;
            margin-bottom: 20px;
        }

        .dot {
            display: inline-block;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: rgba(238, 156, 167, 0.3);
            margin: 0 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .dot.active {
            background: #ee9ca7;
            transform: scale(1.2);
        }

        /* Message Section */
        .message {
            text-align: center;
            margin-bottom: 30px;
            color: #555;
            line-height: 1.8;
        }

        .message h2 {
            font-family: 'Kanit', sans-serif;
            color: #ff6b95;
            font-size: 1.5rem;
            margin-bottom: 15px;
        }

        .message p {
            font-size: 1.05rem;
            margin-bottom: 15px;
        }

        .message .highlight {
            color: #ff6b95;
            font-weight: 500;
        }

        /* Love Button */
        .love-button {
            display: block;
            width: 100%;
            padding: 18px;
            background: linear-gradient(135deg, #ff6b95 0%, #ee4466 100%);
            color: white;
            border: none;
            border-radius: 50px;
            font-family: 'Kanit', sans-serif;
            font-size: 1.3rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 25px rgba(238, 68, 102, 0.3);
            position: relative;
            overflow: hidden;
        }

        .love-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(238, 68, 102, 0.4);
        }

        .love-button:active {
            transform: translateY(-1px);
        }

        .love-button::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.3);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .love-button:hover::before {
            width: 300px;
            height: 300px;
        }

        .love-button span {
            position: relative;
            z-index: 1;
        }

        /* Modal/Popup */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(5px);
            z-index: 1000;
            align-items: center;
            justify-content: center;
            animation: fadeIn 0.3s ease;
        }

        .modal.show {
            display: flex;
        }

        .modal-content {
            background: white;
            padding: 40px 30px;
            border-radius: 25px;
            max-width: 400px;
            width: 90%;
            text-align: center;
            position: relative;
            animation: slideUp 0.5s ease;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .modal-close {
            position: absolute;
            top: 15px;
            right: 15px;
            width: 35px;
            height: 35px;
            background: rgba(238, 156, 167, 0.2);
            border: none;
            border-radius: 50%;
            cursor: pointer;
            font-size: 18px;
            color: #ff6b95;
            transition: all 0.3s ease;
        }

        .modal-close:hover {
            background: rgba(238, 156, 167, 0.3);
            transform: rotate(90deg);
        }

        .modal-hearts {
            font-size: 3rem;
            margin-bottom: 20px;
            animation: heartbeat 1.5s infinite;
        }

        .modal h3 {
            font-family: 'Kanit', sans-serif;
            font-size: 1.8rem;
            color: #ff6b95;
            margin-bottom: 15px;
        }

        .modal p {
            color: #666;
            line-height: 1.8;
            font-size: 1.1rem;
        }

        /* Floating Hearts */
        .floating-hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 2000;
        }

        .floating-heart {
            position: absolute;
            font-size: 40px;
            opacity: 0;
            animation: floatHeart 3s ease-out forwards;
        }

        @keyframes floatHeart {
            0% {
                opacity: 1;
                transform: translateY(0) scale(0);
            }

            50% {
                opacity: 1;
                transform: translateY(-200px) scale(1.2);
            }

            100% {
                opacity: 0;
                transform: translateY(-400px) scale(0.5);
            }
        }

        /* Responsive */
        @media (max-width: 480px) {
            .love-card {
                padding: 30px 20px;
            }

            .header h1 {
                font-size: 1.6rem;
            }

            .slideshow-container {
                height: 250px;
            }

            .message h2 {
                font-size: 1.3rem;
            }

            .message p {
                font-size: 1rem;
            }

            .love-button {
                font-size: 1.1rem;
                padding: 15px;
            }
        }
    </style>
</head>

<body>
    <!-- Background Hearts -->
    <div class="hearts-bg" id="hearts-bg"></div>

    <!-- Main Card -->
    <div class="love-card">
        <!-- Music Control -->
        <button class="music-control playing" id="music-control" onclick="toggleMusic()">
            🎵
        </button>

        <!-- ════════════════════════════════════════════════════════════
             🎵 YOUTUBE MUSIC PLAYER
             แก้ไข: ใส่ YouTube VIDEO ID ที่นี่
             ════════════════════════════════════════════════════════════ -->
        <div id="youtube-player" style="display: none;"></div>

        <!-- Header -->
        <div class="header">
            <h1>💕 ถึงคนที่รักที่สุด 💕</h1>
            <p>For the one who makes my heart smile</p>
        </div>

        <!-- Image Slideshow -->
        <div class="slideshow-container" id="slideshow">
            <div class="slide active">
                <img src="https://media.discordapp.net/attachments/869294644075323412/1466921180425359604/IMG_6110.png?ex=697e804f&is=697d2ecf&hm=b0191785b919bc6923d6cddf83cccba9e8c3094081fc56cce72f22adb4e65ed3&=&format=webp&quality=lossless&width=283&height=350"
                    alt="Our Memory 1">
                <div class="slide-caption">วันที่เราพบกันครั้งแรก 💫</div>
            </div>

            <div class="slide">
                <img src="https://media.discordapp.net/attachments/869294644075323412/1466920169707147509/IMG_6107.png?ex=697e7f5e&is=697d2dde&hm=18e7692d31a4f7241750e93995d780e1720e02463d3b5bd70a9f1a19f4b270da&=&format=webp&quality=lossless&width=664&height=874"
                    alt="Our Memory 2">
                <div class="slide-caption">ทุกช่วงเวลาที่มีเธอ 🌸</div>
            </div>

            <div class="slide">
                <img src="https://media.discordapp.net/attachments/869294644075323412/1466919739765817478/B32D817A-B2E3-43DB-A74B-C8E4D514DFC0.png?ex=697e7ef8&is=697d2d78&hm=5527fe8895585c64ebf2e388ad1910d07269f03dbb34ea75e4dde1ba42fd30f7&=&format=webp&quality=lossless&width=582&height=874"
                    alt="Our Memory 3">
                <div class="slide-caption">คือความสุขที่แท้จริง 💖</div>
            </div>

            <div class="slide">
                <img src="https://media.discordapp.net/attachments/869294644075323412/1466919739371819205/IMG_9669.jpg?ex=697e7ef7&is=697d2d77&hm=db62804fdbc4d9e715dc31c913781d8d363e3103c89dbcc523834d4ab1145127&=&format=webp&width=655&height=874"
                    alt="Our Memory 4">
                <div class="slide-caption">รักเธอทุกวัน 🌹</div>
            </div>
        </div>

        <!-- Slide Dots -->
        <div class="slide-dots" id="slide-dots"></div>

        <!-- Message Section -->
        <div class="message">
            <h2>💝 ความในใจที่อยากบอก</h2>
            <p>
                ตั้งแต่วันที่ได้พบเธอ ชีวิตของฉันเปลี่ยนไป<br>
                เธอทำให้ทุกวันมีความหมาย ทำให้ยิ้มได้ในทุกเช้า
            </p>
            <p>
                ขอบคุณที่เป็น<span class="highlight">แรงบันดาลใจ</span><br>
                ขอบคุณที่เป็น<span class="highlight">ที่พักใจ</span><br>
                ขอบคุณที่เป็น<span class="highlight">ที่สุดของหัวใจ</span>
            </p>
            <p>
                <strong>รักเธอมากกว่าที่คำว่ารักจะบอกได้ 💕</strong>
            </p>
        </div>

        <!-- Love Button -->
        <button class="love-button" onclick="showLoveModal()">
            <span>❤️ เรารักเธอ ❤️</span>
        </button>
    </div>

    <!-- Modal/Popup -->
    <div class="modal" id="love-modal">
        <div class="modal-content">
            <button class="modal-close" onclick="closeLoveModal()">✕</button>
            <div class="modal-hearts">💖💕💗</div>
            <h3>รักเธอนะ</h3>
            <p>
                รักเธอมากกว่าที่คำพูดจะอธิบายได้<br>
                รักเธอทุกวินาที ทุกลมหายใจ<br>
                จะอยู่เคียงข้างเธอเสมอ 🤍
            </p>
        </div>
    </div>

    <!-- Floating Hearts Container -->
    <div class="floating-hearts" id="floating-hearts"></div>

    <!-- YouTube API -->
    <script src="https://www.youtube.com/iframe_api"></script>

    <script>
        // ═══════════════════════════════════════════════════════════════
        // 🎵 ตั้งค่าเพลงที่นี่
        // ═══════════════════════════════════════════════════════════════
        // วิธีหา VIDEO_ID: จาก URL youtube.com/watch?v=OYPiXBIgvJ8
        // เอาตัว OYPiXBIgvJ8 มาใส่
        const YOUTUBE_VIDEO_ID = 'OYPiXBIgvJ8';  // 🔴 ใส่ YouTube Video ID ของคุณ

        // ═══════════════════════════════════════════════════════════════
        // VARIABLES
        // ═══════════════════════════════════════════════════════════════
        let player;
        let musicPlaying = false;
        const musicBtn = document.getElementById('music-control');

        // ═══════════════════════════════════════════════════════════════
        // YOUTUBE PLAYER SETUP
        // ═══════════════════════════════════════════════════════════════
        function onYouTubeIframeAPIReady() {
            player = new YT.Player('youtube-player', {
                height: '0',
                width: '0',
                videoId: YOUTUBE_VIDEO_ID,
                playerVars: {
                    autoplay: 1,
                    controls: 0,
                    loop: 1,
                    playlist: YOUTUBE_VIDEO_ID,
                    enablejsapi: 1,
                    origin: window.location.origin
                },
                events: {
                    'onReady': onPlayerReady,
                    'onStateChange': onPlayerStateChange
                }
            });
        }

        function onPlayerReady(event) {
            // Set volume
            event.target.setVolume(50);  // 50% volume

            // Try to play
            event.target.playVideo();
            musicPlaying = true;
            musicBtn.classList.add('playing');
        }

        function onPlayerStateChange(event) {
            // If video ends, loop it
            if (event.data === YT.PlayerState.ENDED) {
                event.target.playVideo();
            }
        }

        // ═══════════════════════════════════════════════════════════════
        // MUSIC CONTROL
        // ═══════════════════════════════════════════════════════════════
        function toggleMusic() {
            if (!player) return;

            if (musicPlaying) {
                player.pauseVideo();
                musicBtn.textContent = '🔇';
                musicBtn.classList.remove('playing');
            } else {
                player.playVideo();
                musicBtn.textContent = '🎵';
                musicBtn.classList.add('playing');
            }
            musicPlaying = !musicPlaying;
        }

        // ═══════════════════════════════════════════════════════════════
        // BACKGROUND HEARTS
        // ═══════════════════════════════════════════════════════════════
        function createBackgroundHearts() {
            const container = document.getElementById('hearts-bg');
            const heartTypes = ['💕', '💖', '💗', '💝', '💓'];

            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.textContent = heartTypes[Math.floor(Math.random() * heartTypes.length)];
                heart.style.left = Math.random() * 100 + '%';
                heart.style.animationDuration = (Math.random() * 3 + 5) + 's';
                heart.style.fontSize = (Math.random() * 20 + 20) + 'px';

                container.appendChild(heart);

                setTimeout(() => {
                    heart.remove();
                }, 8000);
            }, 800);
        }

        // ═══════════════════════════════════════════════════════════════
        // IMAGE SLIDESHOW
        // ═══════════════════════════════════════════════════════════════
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        const dotsContainer = document.getElementById('slide-dots');

        // Create dots
        slides.forEach((_, index) => {
            const dot = document.createElement('span');
            dot.className = 'dot' + (index === 0 ? ' active' : '');
            dot.onclick = () => goToSlide(index);
            dotsContainer.appendChild(dot);
        });

        const dots = document.querySelectorAll('.dot');

        function showSlide(n) {
            slides.forEach(slide => slide.classList.remove('active'));
            dots.forEach(dot => dot.classList.remove('active'));

            currentSlide = (n + slides.length) % slides.length;
            slides[currentSlide].classList.add('active');
            dots[currentSlide].classList.add('active');
        }

        function nextSlide() {
            showSlide(currentSlide + 1);
        }

        function goToSlide(n) {
            showSlide(n);
        }

        // Auto-change slides every 3.5 seconds
        setInterval(nextSlide, 3500);

        // ═══════════════════════════════════════════════════════════════
        // MODAL
        // ═══════════════════════════════════════════════════════════════
        const modal = document.getElementById('love-modal');

        function showLoveModal() {
            modal.classList.add('show');
            createFloatingHearts();
        }

        function closeLoveModal() {
            modal.classList.remove('show');
        }

        // Close modal on outside click
        modal.addEventListener('click', (e) => {
            if (e.target === modal) {
                closeLoveModal();
            }
        });

        // ═══════════════════════════════════════════════════════════════
        // FLOATING HEARTS ANIMATION
        // ═══════════════════════════════════════════════════════════════
        function createFloatingHearts() {
            const container = document.getElementById('floating-hearts');
            const heartTypes = ['❤️', '💕', '💖', '💗', '💝'];

            for (let i = 0; i < 15; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.className = 'floating-heart';
                    heart.textContent = heartTypes[Math.floor(Math.random() * heartTypes.length)];
                    heart.style.left = Math.random() * 100 + '%';
                    heart.style.animationDelay = Math.random() * 0.5 + 's';

                    container.appendChild(heart);

                    setTimeout(() => {
                        heart.remove();
                    }, 3000);
                }, i * 150);
            }
        }

        // ═══════════════════════════════════════════════════════════════
        // INITIALIZE
        // ═══════════════════════════════════════════════════════════════
        window.addEventListener('load', () => {
            createBackgroundHearts();
        });
    </script>
</body>

</html>
