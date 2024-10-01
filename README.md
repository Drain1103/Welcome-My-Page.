<html lang="my">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prayer Form with Lucky Spin</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-image: url('https://i.postimg.cc/XvSffVf1/photo-2024-10-02-04-06-14.jpg'); /* Updated background image */
            background-size: cover; /* Cover the entire background */
            background-position: center; /* Center the image */
            text-align: center;
            padding: 50px;
        }
        form {
            background-color: rgba(255, 255, 255, 0.8); /* White background with transparency */
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
        #spinCircle {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            position: relative;
            margin: 20px auto;
            overflow: hidden;
        }
        .segment {
            position: absolute;
            width: 50%;
            height: 50%;
            border-radius: 0 100% 0 0; /* Only top right rounded */
            transform-origin: 100% 100%;
            color: white; /* Text color */
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 16px;
        }
        .segment:nth-child(1) { background: linear-gradient(135deg, #ff7e5f, #feb47b); } /* 5000 MMK */
        .segment:nth-child(2) { background: linear-gradient(135deg, #6a11cb, #2575fc); } /* 6000 MMK */
        .segment:nth-child(3) { background: linear-gradient(135deg, #00c6ff, #0072ff); } /* 7000 MMK */
        .segment:nth-child(4) { background: linear-gradient(135deg, #ff6a00, #ee0979); } /* 8000 MMK */
        .segment:nth-child(5) { background: linear-gradient(135deg, #ff3f20, #ff8c00); } /* 9000 MMK */
        .segment:nth-child(6) { background: linear-gradient(135deg, #43e97b, #38f9d7); } /* 10000 MMK */
        .result {
            margin-top: 20px;
            font-size: 24px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>🌸✨ မြန်မာ့ရိုးရာသီတင်းကျွတ်ပွဲတော် မှကြိုဆိုပါတယ်! 🎉🌙</h1>
    <p>ကျန်းမာချမ်းသာမှုအပြည့်နှင့်အေးချမ်းပျော်ရွှင်စရာအချိန်တစ်ခုဖြစ်ပါစေ။</p>
    
    <form id="prayerForm">
        <label for="name">နာမည် :</label><br>
        <input type="text" id="name" name="name" required><br><br>
        
        <label for="prayer">🌸✨ အကိုကြီးအတွက် ဆုတောင်းစကား ✨🌸 :</label><br>
        <textarea id="prayer" name="prayer" rows="4" cols="50" placeholder="🌕✨ သီတင်းကျွတ်အတွက် ဆုတောင်းစကား ✨🌕" required></textarea><br><br>
        
        <input type="submit" value="ပေးပို့ရန်">
    </form>

    <div class="message" id="successMessage" style="display: none;"></div>
    <div id="spinCircle">
        <div class="segment" style="transform: rotate(0deg);">5000ရသည်</div>
        <div class="segment" style="transform: rotate(60deg);">6000 ရသည်</div>
        <div class="segment" style="transform: rotate(120deg);">7000 ရသည်</div>
        <div class="segment" style="transform: rotate(180deg);">8000 ရသည်</div>
        <div class="segment" style="transform: rotate(240deg);">9000ရသည်</div>
        <div class="segment" style="transform: rotate(300deg);">10000 ရသည်</div>
    </div>

    <div class="result" id="result"></div>

    <script>
        document.getElementById('prayerForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent the form from submitting in the traditional way

            // Display the success message
            var successMessage = document.getElementById('successMessage');
            successMessage.innerHTML = "✨ ကျေးဇူးတင်ပါသည်! 💌 မင်းရဲ့ ဆုတောင်းစာ ပို့ပြီးပြီ။ 💌✨";
            successMessage.style.display = "block";

            // Start the spin effect
            const spinCircle = document.getElementById('spinCircle');
            const randomRotation = Math.floor(Math.random() * 360) + 3600; // Spins multiple full rotations

            // Add spinning effect
            spinCircle.style.transition = "transform 4s ease-out";
            spinCircle.style.transform = `rotate(${randomRotation}deg)`;

            // Calculate reward based on rotation
            setTimeout(() => {
                const rewardIndex = Math.floor((randomRotation % 360) / 60); // Get segment based on rotation
                const rewards = [5000, 6000, 7000, 8000, 9000, 10000];
                const reward = rewards[rewardIndex];

                // Display the reward
                document.getElementById('result').innerText = `🎉 မုန့်ဖိုး: ${reward}ရသည် `;
            }, 4000); // Wait for the animation to finish

            // Optionally, clear the form fields after a short delay
            setTimeout(() => {
                this.reset();
                spinCircle.style.transform = 'rotate(0deg)'; // Reset the spin animation
                successMessage.style.display = "none"; // Hide the success message
                document.getElementById('result').innerText = ''; // Clear the result
            }, 6000); // Adjust time as needed (20 seconds here)
        });
    </script>
</body>
</html>
