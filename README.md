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

<h5 style="cursor: pointer;">2 Cambiar al idioma de Inglés</h5>

<script>
    var modal = document.getElementById("myModal");
    var span = document.getElementsByClassName("close")[0];

    var originalText = {
        title: "¡Bienvenidos a Tiktok Shop!",
        subtitle: "¿Estás listo para trabajar?",
        helpText: "¡Elige la ayuda que necesitas!",
        loginLink: "1 Para volver a acceder a su cuenta",
        modalMessage: "Una vez que haya completado su registro por primera vez, podrá iniciar sesión fácilmente en su cuenta utilizando este enlace.",
        loginButton: "Iniciar sesión aquí",
        changeLanguageText: "2 Cambiar al idioma de Inglés"
    };

    var englishText = {
        title: "🎈🌼 Welcome to Tiktok Shop! 🌼🎈",
        subtitle: "🛍️✨ Are you ready to work? ✨🛍️",
        helpText: "🌈✨ Choose the help you need! ✨🌈",
        loginLink: "1 Click here to log in to your account",
        modalMessage: "Once you have completed your registration for the first time, you can easily log in to your account using this link.",
        loginButton: "Log in here",
        changeLanguageText: "2 Change to Spanish"
    };

    var isEnglish = false;

    function changeLanguage() {
        if (isEnglish) {
            // Switch back to original language
            document.querySelector("header h1").textContent = originalText.title;
            document.querySelector("header h2").textContent = originalText.subtitle;
            document.querySelector("header h3").textContent = originalText.helpText;
            document.getElementById("login-link").textContent = originalText.loginLink;
            document.getElementById("login-url").textContent = originalText.loginButton;
            document.querySelector(".modal-content p").textContent = originalText.modalMessage;
            document.querySelector("h5").textContent = originalText.changeLanguageText;
        } else {
            // Switch to English
            document.querySelector("header h1").textContent = englishText.title;
            document.querySelector("header h2").textContent = englishText.subtitle;
            document.querySelector("header h3").textContent = englishText.helpText;
            document.getElementById("login-link").textContent = englishText.loginLink;
            document.getElementById("login-url").textContent = englishText.loginButton;
            document.querySelector(".modal-content p").textContent = englishText.modalMessage;
            document.querySelector("h5").textContent = englishText.changeLanguageText;
        }

        isEnglish = !isEnglish; // Toggle the language state
    }

    document.getElementById("login-link").addEventListener('click', function() {
        // Change to English when the login link is clicked
        if (!isEnglish) {
            changeLanguage();
        }
        document.querySelector(".modal-content p").textContent = englishText.modalMessage;
        document.getElementById("login-url").textContent = englishText.loginButton;
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

    document.querySelector("h5").addEventListener('click', changeLanguage);
</script>

</body>
</html>
