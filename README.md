<!DOCTYPE html>
<html lang="my">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prayer Form with Lucky Spin and Fireworks</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-image: url('https://i.postimg.cc/XvSffVf1/photo-2024-10-02-04-06-14.jpg');
            background-size: cover;
            background-position: center;
            text-align: center;
            padding: 50px;
            margin: 0;
            overflow: auto; /* Allow scrolling */
        }
        form {
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            padding: 20px;
            max-width: 500px;
            margin: auto;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
        }
        input, textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        input[type="submit"] {
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        input[type="submit"]:hover {
            background-color: #45a049;
        }
        .message {
            margin-top: 20px;
            color: green;
            font-weight: bold;
        }
        canvas {
            position: absolute;
            top: 0;
            left: 0;
            pointer-events: none;
        }

        /* Lucky Spin Styles */
        .container {
            text-align: center;
        }
        .wheel {
            width: 300px;
            height: 300px;
            border-radius: 50%;
            border: 10px solid #d4af37;
            position: relative;
            overflow: hidden;
            margin-bottom: 20px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
            transition: transform 2s ease-out;
        }
        .segment {
            position: absolute;
            width: 50%;
            height: 50%;
            text-align: center;
            line-height: 120px;
            font-size: 24px;
            font-weight: bold;
            color: #fff;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);
            transform-origin: 100% 100%;
            overflow: hidden;
        }
        .segment-1 { background: linear-gradient(45deg, #ff7e5f, #feb47b); transform: rotate(0deg); }
        .segment-2 { background: linear-gradient(45deg, #86e3ce, #65a8e5); transform: rotate(60deg); }
        .segment-3 { background: linear-gradient(45deg, #fdc830, #f37335); transform: rotate(120deg); }
        .segment-4 { background: linear-gradient(45deg, #5f72be, #99b3e0); transform: rotate(180deg); }
        .segment-5 { background: linear-gradient(45deg, #ff5f6d, #ffc371); transform: rotate(240deg); }
        .segment-6 { background: linear-gradient(45deg, #6a11cb, #2575fc); transform: rotate(300deg); }
        .reward {
            position: absolute;
            width: 100%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        button {
            padding: 12px 24px;
            font-size: 18px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #218838;
        }
        .result {
            margin-top: 20px;
            font-size: 24px;
            font-weight: bold;
            color: #333;
        }
    </style>
</head>
<body>
    <canvas id="fireworksCanvas"></canvas>

    <h1 style="margin-bottom: 30px;">🌸✨ မြန်မာ့ရိုးရာသီတင်းကျွတ်ပွဲတော် မှကြိုဆိုပါတယ်! 🎉🌙</h1>
    <p>ကျန်းမာချမ်းသာမှုအပြည့်နှင့်အေးချမ်းပျော်ရွှင်စရာအချိန်တစ်ခုဖြစ်ပါစေ။</p>
    
    <form id="prayerForm">
        <label for="name">နာမည် :</label><br>
        <input type="text" id="name" name="name" required><br><br>
        
        <label for="prayer">🌸✨ အကိုကြီးအတွက် ဆုတောင်းစကား ✨🌸 :</label><br>
        <textarea id="prayer" name="prayer" rows="4" cols="50" placeholder="🌕✨ သီတင်းကျွတ်အတွက် ဆုတောင်းစကား ✨🌕" required></textarea><br><br>
        
        <input type="submit" value="ပေးပို့ရန်">
    </form>

    <div class="message" id="successMessage" style="display: none;"></div>

    <div class="container" style="display: none;" id="spinContainer">
        <h1>🌺✨ သီတင်းကျွတ်မုန်းဖိုးယူကြမယ် ✨🌺
</h1>
        <div class="wheel" id="wheel">
            <div class="segment segment-1"><div class="reward">🌼 5000 🌼</div></div>
            <div class="segment segment-2"><div class="reward">🌸 6000 🌸</div></div>
            <div class="segment segment-3"><div class="reward">🌻 7000 🌻</div></div>
            <div class="segment segment-4"><div class="reward">🎉 8000 🎉</div></div>
            <div class="segment segment-5"><div class="reward">🎊 9000 🎊</div></div>
            <div class="segment segment-6"><div class="reward">🌟 10000 🌟</div></div>
        </div>
        <button id="spinButton">🌈✨ ကံစစ်းကြည့်ပါ ✨🌈
</button>
        <div class="result" id="result"></div>
    </div>

    <script>
        document.getElementById('prayerForm').addEventListener('submit', function(event) {
            event.preventDefault();
            this.style.display = "none";

            const spinContainer = document.getElementById('spinContainer');
            spinContainer.style.display = "block"; // Show the lucky spin container

            var successMessage = document.getElementById('successMessage');
            successMessage.innerHTML = "✨ ကျေးဇူးတင်ပါသည်! 💌 မင်းရဲ့ ဆုတောင်းစာ ပို့ပြီးပြီ။ 💌✨";
            successMessage.style.display = "block";
        });

        let spinCount = 0;
        document.getElementById('spinButton').addEventListener('click', function() {
            const wheel = document.getElementById('wheel');
            const resultDisplay = document.getElementById('result');
            spinCount++;

            let randomDegree;
            if (spinCount === 9) {
                randomDegree = 2880;
            } else {
                randomDegree = Math.floor(Math.random() * 360) + 720;
            }

            wheel.style.transform = `rotate(${randomDegree}deg)`;

            setTimeout(() => {
                const totalSegments = 6;
                const segmentDegree = 360 / totalSegments;
                const finalDegree = randomDegree % 360;

                let resultIndex = Math.floor((finalDegree + (segmentDegree / 2)) / segmentDegree) % totalSegments;
                const rewards = ['🌼 5000 🌼', '🌸 6000 🌸', '🌻 7000 🌻', '🎉 8000 🎉', '🎊 9000 🎊', '🌟 10000 🌟'];

                resultDisplay.textContent = `🌟 🎀 မုန့်ဖိုး 🎀 🌟
: ${spinCount === 9 ? rewards[5] : rewards[resultIndex]}`;
            }, 2000);
        });

        const canvas = document.getElementById('fireworksCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        
        // Fireworks logic
    </script>
</body>
</html>
