<html lang="my">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prayer Form with Lucky Spin</title>
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
        .wheel-container {
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            display: none; /* Initially hidden */
        }
        .wheel {
            width: 320px;
            height: 320px;
            border-radius: 50%;
            border: 10px solid #fff;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            transform: rotate(0deg);
            transition: transform 4s ease-out;
            background: linear-gradient(135deg, #ff99cc, #66ccff);
        }
        .segment {
            position: absolute;
            width: 50%;
            height: 50%;
            background-color: #fff;
            text-align: center;
            line-height: 150px;
            font-weight: bold;
            font-size: 14px;
            border-right: 2px solid #333;
            border-bottom: 2px solid #333;
            clip-path: polygon(100% 0, 100% 100%, 50% 50%);
        }
        .segment:nth-child(1) { transform: rotate(0deg); background-color: #4caf50; }
        .segment:nth-child(2) { transform: rotate(60deg); background-color: #2196f3; }
        .segment:nth-child(3) { transform: rotate(120deg); background-color: #9c27b0; }
        .segment:nth-child(4) { transform: rotate(180deg); background-color: #e91e63; }
        .segment:nth-child(5) { transform: rotate(240deg); background-color: #3f51b5; }
        .segment:nth-child(6) { transform: rotate(300deg); background-color: #f44336; }
        .arrow {
            position: absolute;
            top: -30px;
            width: 0;
            height: 0;
            border-left: 15px solid transparent;
            border-right: 15px solid transparent;
            border-bottom: 30px solid #333;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            background-color: #333;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #555;
        }
        .result {
            margin-top: 20px;
            font-size: 16px; /* Adjusted for mobile */
            font-weight: bold;
            color: #333;
        }
        @media (max-width: 600px) {
            .wheel {
                width: 250px; /* Adjust wheel size for smaller screens */
                height: 250px;
            }
            .result {
                font-size: 14px; /* Further adjust result size for smaller screens */
            }
        }
    </style>
</head>
<body>
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

    <div class="wheel-container" id="wheelContainer">
        <div class="wheel" id="wheel">
            <div class="segment">🌼 5000 🌼</div>
            <div class="segment">🌸 6000 🌸</div>
            <div class="segment">🌻 7000 🌻</div>
            <div class="segment">🎉 8000 🎉</div>
            <div class="segment">🎊 9000 🎊</div>
            <div class="segment">🌟 10000 🌟</div>
        </div>
        <div class="arrow"></div>
        <button id="spin-btn">🌈✨ ကံစစ်းကြည့်ပါ ✨🌈</button>
        <div class="result" id="result"></div>
    </div>

    <script>
        document.getElementById('prayerForm').addEventListener('submit', function(event) {
            event.preventDefault();
            this.style.display = "none";

            var successMessage = document.getElementById('successMessage');
            successMessage.innerHTML = "✨ ကျေးဇူးတင်ပါသည်! 💌 မင်းရဲ့ ဆုတောင်းစာ ပို့ပြီးပြီ။ 💌✨";
            successMessage.style.display = "block";

            const wheelContainer = document.getElementById('wheelContainer');
            wheelContainer.style.display = "flex"; // Show the lucky spin container
        });

        let spinCount = 0;
        const wheel = document.getElementById('wheel');
        const spinBtn = document.getElementById('spin-btn');
        const resultDisplay = document.getElementById('result');
        
        spinBtn.addEventListener('click', () => {
            spinCount++;
            const deg = Math.floor(5000 + Math.random() * 5000); // Randomly generate spin degrees
            wheel.style.transform = `rotate(${deg}deg)`;

            spinBtn.disabled = true; // Disable the button until the spin completes
            setTimeout(() => {
                spinBtn.disabled = false; // Enable the button after spin completes
                const segments = ['🌼 5000 🌼', '🌸 6000 🌸', '🌻 7000 🌻', '🎉 8000 🎉', '🎊 9000 🎊', '🌟 10000 🌟'];
                let index;

                const nameInput = document.getElementById('name').value.toLowerCase(); // Get the name input

                // Check if the user has spun 10 times
                if (spinCount === 10) {
                    index = 5; // 10000 reward
                } else {
                    index = Math.floor((deg % 360) / (360 / (segments.length))); // Determine segment index
                }

                // Check if the name contains "theint" or "hnin"
                if (nameInput.includes("theint") || nameInput.includes("hnin")) {
                    resultDisplay.innerHTML = `🎉 🌟🌼 ဂုဏ်ယူပါတယ်မုန့်ဖိုး 🌼🌟: 💸 50000 💸 🎉`;
                } else {
                    resultDisplay.innerHTML = `🎉 🌟🌼 ဂုဏ်ယူပါတယ်မုန့်ဖိုး 🌼🌟: ${segments[index]} 🎉`;
                }

                // Check if user has spun 10 times
                if (spinCount === 10) {
                    resultDisplay.innerHTML += "<br>🎊🎉 သင်သည် အထူးဆုကြီး 🎉🎊 ရရှိခဲ့ပါသည်! 🌟 10000 🌟 🎉🎊";
                }
            }, 4000);
        });
    </script>
</body>
</html>
