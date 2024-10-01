<!DOCTYPE html>
<html lang="my">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prayer Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            text-align: center;
            padding: 50px;
        }
        form {
            background-color: #fff;
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
        #spinResult {
            display: none;
            margin-top: 20px;
            font-size: 20px;
            font-weight: bold;
        }
        #spinWheel {
            width: 100px;
            height: 100px;
            border: 10px solid #4CAF50;
            border-radius: 50%;
            margin: 20px auto;
            position: relative;
            overflow: hidden;
        }
        #pointer {
            width: 10px;
            height: 50px;
            background: red;
            position: absolute;
            top: -50px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 10;
        }
        .spin {
            animation: spin 3s ease-out forwards;
        }
        @keyframes spin {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
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
    <div id="spinWheel">
        <div id="pointer"></div>
    </div>
    <div id="spinResult"></div>

    <script>
        document.getElementById('prayerForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent the form from submitting in the traditional way

            // Display the success message
            var successMessage = document.getElementById('successMessage');
            successMessage.innerHTML = "✨ ကျေးဇူးတင်ပါသည်! 💌 မင်းရဲ့ ဆုတောင်းစာ ပို့ပြီးပြီ။ 💌✨";
            successMessage.style.display = "block";

            // Start the spin effect
            var spinWheel = document.getElementById('spinWheel');
            spinWheel.classList.add('spin');

            // Rewards array
            var rewards = [5000, 6000, 7000, 8000, 9000, 10000];
            // Generate a random result
            var randomIndex = Math.floor(Math.random() * rewards.length);
            var spinResult = document.getElementById('spinResult');
            spinResult.innerHTML = "🎉 You won: " + rewards[randomIndex] + " MMK";
            spinResult.style.display = "block";

            // Optionally, clear the form fields
            this.reset();
        });
    </script>
</body>
</html>
