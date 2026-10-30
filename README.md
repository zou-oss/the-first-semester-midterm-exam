<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Màn Hình Hoạt Ảnh</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body, html {
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000; 
            cursor: pointer; /* Biến chuột thành hình bàn tay để báo hiệu có thể click */
        }

        .fullscreen-video {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            min-width: 100%;
            min-height: 100%;
            width: auto;
            height: auto;
            object-fit: cover;
        }

        /* Dòng chữ nhỏ gợi ý người dùng bấm để bật tiếng (sẽ tự ẩn đi sau khi bấm) */
        .audio-hint {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            color: rgba(255, 255, 255, 0.6);
            font-family: sans-serif;
            font-size: 14px;
            pointer-events: none; /* Không làm cản trở cú click */
            transition: opacity 0.5s;
        }
    </style>
</head>
<body>

    <video id="myVideo" class="fullscreen-video" autoplay loop muted playsinline>
        <source src="animation.mp4" type="video/mp4">
        Trình duyệt của bạn không hỗ trợ xem video này.
    </video>

    <div id="hintText" class="audio-hint">Chạm vào màn hình để bật âm thanh 🔊</div>

    <script>
        const video = document.getElementById('myVideo');
        const hintText = document.getElementById('hintText');

        // Khi người dùng click hoặc chạm vào bất kỳ đâu trên màn hình
        document.addEventListener('click', function() {
            if (video.muted) {
                video.muted = false; // Bật âm thanh
                hintText.style.opacity = '0'; // Ẩn dòng chữ gợi ý đi
            }
        });
    </script>

</body>
</html>
