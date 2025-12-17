<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Anniversary 💖</title>
    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --pink: #ffb7c5;
            --dark-pink: #f08080;
            --bg: #fff5f7;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: var(--bg);
            margin: 0;
            flex-direction: column;
            overflow: hidden;
            font-family: 'Sarabun', sans-serif;
        }

        .envelope-wrapper {
            position: relative;
            width: 300px;
            height: 200px;
            cursor: pointer;
            z-index: 10;
        }

        .envelope {
            position: relative;
            width: 100%;
            height: 100%;
            background-color: var(--pink);
            border-radius: 0 0 8px 8px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }

        /* ฝาซอง */
        .top-flap {
            position: absolute;
            top: 0;
            width: 0;
            height: 0;
            border-left: 150px solid transparent;
            border-right: 150px solid transparent;
            border-top: 100px solid #ffdae0;
            transform-origin: top;
            transition: all 0.6s ease;
            z-index: 50;
        }

        /* ตัวการ์ด */
        .card {
            position: absolute;
            bottom: 10px;
            left: 10px;
            width: 280px;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            transition: all 1s ease;
            z-index: 5; /* อยู่หลังซองตอนแรก */
            text-align: center;
            box-sizing: border-box;
            opacity: 0;
        }

        .text-header {
            font-size: 22px;
            font-weight: bold;
            color: var(--dark-pink);
            display: block;
            margin-bottom: 10px;
        }

        .text-body {
            font-size: 14px;
            color: #555;
            line-height: 1.5;
        }

        /* เมื่อเปิดซอง */
        .envelope-wrapper.open .top-flap {
            transform: rotateX(180deg);
            z-index: 1; /* ให้ฝาไปอยู่หลังสุด */
        }

        .envelope-wrapper.open .card {
            transform: translateY(-240px); /* ดึงการ์ดขึ้นมาสูงๆ */
            opacity: 1;
            z-index: 100; /* ให้การ์ดมาอยู่หน้าสุด */
        }

        /* หัวใจลอย */
        .heart {
            position: fixed;
            bottom: -50px;
            font-size: 24px;
            animation: float 4s linear forwards;
            z-index: 999;
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0); opacity: 1; }
            100% { transform: translateY(-120vh) rotate(360deg); opacity: 0; }
        }

        .instruction {
            margin-top: 40px;
            color: var(--dark-pink);
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="envelope-wrapper" id="wrapper">
        <div class="top-flap"></div>
        <div class="card">
            <span class="text-header">Happy 2nd Month</span>
            <span class="text-body">
                สวัสดีอ้วน วันนี้ครบสองเดือนอีกแล้วไวมากเลยอ้วนว่ามั้ย เดือนนี้ทั้งเบบี้แล้วก็เค้าเราสองคนโตขึ้นกันทั้งคู่เลย ต่างคนต่างมีหน้าที่เป็นของตัวเองแล้วเบบี้คนเก่งของเค้าก็ทำมันได้ดีมาก อยากบอกเบบี้ว่าอยากให้เบบี้ยิ้มหวานแฮปปี้ทุกวัน ช่วงนี้เบบี้ทำงานเหนื่อยทุกวันเลย อยากให้เธอพักผ่อนเยอะเยอะ ไม่ว่าอะไรจะใจร้ายกับเธอจะมีเค้าอยู่ตรงนี้ตลอด เค้ารอกอดเธอตรงนี้เสมอเลย เค้ารักเบบี้มากมากเลย สุขสันต์วันครบรอบสองเดือนค่ะ
            </span>
            <br><br>
            <span style="color:var(--pink); font-style: italic;">love u baby.</span>
        </div>
        <div class="envelope"></div>
    </div>

    <p class="instruction" id="hint">click me! ❤️</p>

    <script>
        const wrapper = document.getElementById('wrapper');
        const hint = document.getElementById('hint');
        let heartInterval;

        wrapper.addEventListener('click', () => {
            if (!wrapper.classList.contains('open')) {
                wrapper.classList.add('open');
                hint.style.opacity = '0';
                
                // เริ่มปล่อยหัวใจทันที
                heartInterval = setInterval(createHeart, 300);
            }
        });

        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            // สุ่มสีชมพูโทนต่างๆ
            const colors = ['#ffb7c5', '#f08080', '#ffc0cb', '#ff69b4'];
            heart.style.color = colors[Math.floor(Math.random() * colors.length)];
            
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 4000);
        }
    </script>
</body>
</html>
