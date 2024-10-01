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
    </style>
</head>
<body>
    <h1>🌸✨ မြန်မာ့ရိုးရာသီတင်းကျွတ်ပွဲတော် မှကြိုဆိုပါတယ်! 🎉🌙</h1>
    <p>ကျန်းမာချမ်းသာမှုအပြည့်နှင့်အေးချမ်းပျော်ရွှင်စရာအချိန်တစ်ခုဖြစ်ပါစေ။</p>
    
    <form action="/submit-prayer" method="post">
        <label for="name">နာမည် :</label><br>
        <input type="text" id="name" name="name" required><br><br>
        
        <label for="prayer">🌸✨ အကိုကြီးအတွက် ဆုတောင်းစကား ✨🌸 :</label><br>
        <textarea id="prayer" name="prayer" rows="4" cols="50" placeholder="🌕✨ သီတင်းကျွတ်အတွက် ဆုတောင်းစကား ✨🌕" required></textarea><br><br>
        
        <input type="submit" value="ပေးပို့ရန်">
    </form>
</body>
</html>
