<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible=IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chào mừng Ngày Nhà giáo Việt Nam 20/11</title>
    <style>
        body {
            font-family: 'Times New Roman', serif;
            line-height: 1.6;
            background-color: #fdf5e6;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #f39c12;
            color: white;
            text-align: center;
            padding: 20px 0;
        }
        nav {
            text-align: center;
            margin: 15px 0;
        }
        nav a {
            margin: 0 10px;
            text-decoration: none;
            color: #333;
        }
        section {
            padding: 20px;
            margin: 20px auto;
            max-width: 800px;
            background-color: #fff8dc;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        footer {
            text-align: center;
            padding: 10px;
            background-color: #f39c12;
            color: white;
            position: fixed;
            width: 100%;
            bottom: 0;
        }
        #card-output {
            border: 2px solid #f39c12;
            padding: 15px;
            margin-top: 15px;
            background-color: #fff;
            border-radius: 8px;
        }
        .form-group {
            margin-bottom: 10px;
        }
        #card-output img {
            max-width: 100%;
            height: auto;
            margin-top: 10px;
        }
        .button-group {
            margin-top: 20px;
            text-align: center;
        }
        .button-group button {
            padding: 10px 20px;
            margin: 10px;
            border: none;
            background-color: #f39c12;
            color: white;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/0.4.1/html2canvas.min.js"></script>
    <script>
        function createCard() {
            const name = document.getElementById('name').value;
            const message = document.getElementById('message').value;
            const imageInput = document.getElementById('image-input').files[0];
            const cardOutput = document.getElementById('card-output');
            
            let cardContent = `
                <h3>Thiệp chúc mừng</h3>
                <p><strong>Gửi đến:</strong> ${name}</p>
                <p><strong>Lời chúc:</strong> ${message}</p>
            `;

            if (imageInput) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    cardContent += <img src="${e.target.result}" alt="Hình ảnh chúc mừng">;
                    cardOutput.innerHTML = cardContent;
                };
                reader.readAsDataURL(imageInput);
            } else {
                cardOutput.innerHTML = cardContent;
            }
        }

        function saveCard() {
            html2canvas(document.getElementById('card-output')).then(function(canvas) {
                const link = document.createElement('a');
                link.href = canvas.toDataURL("image/png");
                link.download = 'thiep-chuc-mung-20-11.png';
                link.click();
            });
        }

        function shareCard() {
            const cardContent = document.getElementById('card-output').innerHTML;
            const shareText = encodeURIComponent(cardContent);
            const shareUrl = https://www.facebook.com/sharer/sharer.php?u=${shareText};
            window.open(shareUrl, '_blank');
        }
    </script>
</head>
<body>

    <header>
        <h1>Chào mừng Ngày Nhà giáo Việt Nam 20/11</h1>
    </header>

    <nav>
        <a href="#y-nghia">Ý nghĩa</a>
        <a href="#loi-chuc">Lời chúc</a>
        <a href="#hoat-dong">Hoạt động</a>
        <a href="#tao-thiep">Tạo thiệp</a>
    </nav>

    <section id="y-nghia">
        <h2>Ý nghĩa Ngày Nhà giáo Việt Nam</h2>
        <p>Ngày 20/11 là dịp để tri ân các thầy cô giáo, những người đã cống hiến hết mình cho sự nghiệp trồng người. Đây là thời điểm để học sinh, sinh viên và phụ huynh gửi lời cảm ơn chân thành đến những người thầy đã dạy dỗ, dìu dắt thế hệ trẻ.</p>
    </section>

    <section id="loi-chuc">
        <h2>Lời chúc đến các thầy cô</h2>
        <p>Xin gửi đến các thầy cô những lời chúc tốt đẹp nhất: Chúc thầy cô luôn mạnh khỏe, hạnh phúc và tiếp tục thành công trong sự nghiệp giáo dục.</p>
    </section>

    <section id="tao-thiep">
        <h2>Tạo thiệp chúc mừng</h2>
        <div class="form-group">
            <label for="name">Tên người nhận:</label><br>
            <input type="text" id="name" placeholder="Nhập tên thầy/cô" required>
        </div>
        <div class="form-group">
            <label for="message">Lời chúc:</label><br>
            <textarea id="message" placeholder="Nhập lời chúc của bạn" rows="4" required></textarea>
        </div>
        <div class="form-group">
            <label for="image-input">Chọn hình ảnh:</label><br>
            <input type="file" id="image-input" accept="image/*">
        </div>
        <button onclick="createCard()">Tạo thiệp</button>

        <div id="card-output"></div>

        <div class="button-group">
            <button onclick="saveCard()">Lưu thiệp</button>
            <button onclick="shareCard()">Chia sẻ thiệp</button>
        </div>


</body>
</html>
