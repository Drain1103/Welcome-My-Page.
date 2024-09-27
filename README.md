<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Portfolio</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }
        header {
            background: #333;
            color: white;
            padding: 20px;
            text-align: center;
        }
        nav a {
            margin: 0 15px;
            color: white;
            text-decoration: none;
        }
        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 15px;
            padding: 20px;
        }
        .modal {
            display: none;
            position: fixed;
            z-index: 1;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0,0,0,0.5);
        }
        .modal-content {
            background-color: #fefefe;
            margin: 15% auto;
            padding: 20px;
            border: 1px solid #888;
            width: 80%;
            max-width: 500px;
            text-align: center;
        }
        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }
        .close:hover,
        .close:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }
        #login-url {
            display: inline-block;
            margin-top: 15px;
            padding: 10px 20px;
            background-color: #333;
            color: white;
            text-decoration: none;
            border-radius: 5px;
        }
        #login-url:hover {
            background-color: #555;
        }
    </style>
</head>
<body>

<header>
    <h1>🎈🌼 ¡Bienvenidos a Tiktok Shop! 🌼🎈</h1>
    <h2>🛍️✨ ¿Estás listo para trabajar? ✨🛍️</h2>
    <h3>🌈✨ ¡Elige la ayuda que necesitas! ✨🌈</h3>
    <h4 id="login-link" style="cursor: pointer;">1 Para volver a acceder a su cuenta</h4>
</header>

<main class="grid-container">
    <!-- Project items are hidden -->
</main>

<div id="myModal" class="modal">
    <div class="modal-content">
        <span class="close">&times;</span>
        <h2>Detalles</h2>
        <p></p>
        <a id="login-url" href="#" target="_blank"></a>
        <br>
        <img src="https://i.postimg.cc/XJZZD9Hs/photo-2024-09-28-04-17-48.jpg" alt="Descriptive Image of Tiktok Shop" style="max-width: 100%; height: auto;">
    </div>
</div>

<h5 style="cursor: pointer;">2 Cambiar al idioma de Myanmar</h5>

<script>
    var modal = document.getElementById("myModal");
    var span = document.getElementsByClassName("close")[0];

    document.getElementById("login-link").addEventListener('click', function() {
        document.querySelector(".modal-content p").textContent = "Una vez que haya completado su registro por primera vez, podrá iniciar sesión fácilmente en su cuenta utilizando este enlace.";
        document.getElementById("login-url").textContent = "Iniciar sesión aquí";
        document.getElementById("login-url").href = "https://pedfgs.com/m/login";
        modal.style.display = "block";
    });

    span.onclick = function() {
        modal.style.display = "none";
    }

    window.onclick = function(event) {
        if (event.target == modal) {
            modal.style.display = "none";
        }
    }

    function changeLanguageToMyanmar() {
        document.querySelector("header h1").textContent = "🎈🌼 Tiktok Shop မှ ကြိုဆိုပါတယ်! 🌼🎈";
        document.querySelector("header h2").textContent = "🛍️✨ သင်အလုပ်လုပ်ရန် အသင့်ဖြစ်ပါသလား? ✨🛍️";
        document.querySelector("header h3").textContent = "🌈✨ သင်လိုအပ်သောအကူအညီကို ရွေးချယ်ပါ! ✨🌈";
        document.getElementById("login-link").textContent = "1 သင်၏အကောင့်သို့ ပြန်ဝင်ရန်";
        document.getElementById("login-url").textContent = "ဒီမှာ ဝင်ပါ";
        document.querySelector(".modal-content p").textContent = "သင်သည် ပထမဆုံးမှတ်ပုံတင်မှုကို အပြီးသတ်ပြီးပါက သင့်အကောင့်သို့ အလွယ်တကူ ဝင်ရောက်နိုင်ပါသည်။";
        document.querySelector("h5").textContent = "2 မြန်မာဘာသာစကားသို့ပြောင်းပါ";
    }

    document.querySelector("h5").addEventListener('click', changeLanguageToMyanmar);
</script>

</body>
</html>
