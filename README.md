<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Portfolio</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-image: url('https://i.postimg.cc/SR4GFyX2/photo-2024-09-28-06-42-05.jpg');
            background-size: cover;
            background-position: center;
            height: 100vh;
            color: white;
        }
        header {
            background: rgba(0, 0, 0, 0.7);
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
            background-color: rgba(0, 0, 0, 0.5);
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
        .original-text {
            display: none; /* Initially hide the original text */
            margin-top: 10px;
        }
    </style>
</head>
<body>

<header>
    <h1 id="welcome-title">🎈🌼 ¡Bienvenidos a Tiktok Shop! 🌼🎈</h1>
    <h2 id="ready-text">🛍️✨ ¿Estás listo para trabajar? ✨🛍️</h2>
    <h3 id="choose-help">🌈✨ ¡Elige la ayuda que necesitas! ✨🌈</h3>
    <h4 id="login-link" style="cursor: pointer;">1 Para volver a acceder a su cuenta</h4>
    <h4 id="register-link" style="cursor: pointer;">2 Fácilmente para registrarse</h4>
    <div id="original-login-text" class="original-text">Detalles de acceso.</div>
    <div id="original-register-text" class="original-text">Proceso de registro.</div>
</header>

<div class="grid-container">
    <!-- Project items are hidden -->
</div>

<!-- Modal for Login -->
<div id="myModal" class="modal">
    <div class="modal-content">
        <span class="close">&times;</span>
        <h2>Detalles</h2>
        <p id="modal-message">Una vez que haya completado su registro por primera vez, podrá iniciar sesión fácilmente en su cuenta utilizando este enlace.</p>
        <a id="login-url" href="https://pedfgs.com/m/login" target="_blank">Iniciar sesión aquí</a>
        <br>
        <img src="https://i.postimg.cc/XJZZD9Hs/photo-2024-09-28-04-17-48.jpg" alt="Descriptive Image" style="max-width: 100%; height: auto;">
    </div>
</div>

<!-- Modal for Registration -->
<div id="registerModal" class="modal">
    <div class="modal-content">
        <span class="close">&times;</span>
        <h2>Registro</h2>
        <p>✨ ¡Haga clic en este enlace para registrarse directamente y crear su cuenta inmediatamente!</p>
        <a href="https://pedfgs.com/m/register" target="_blank">Registrarse aquí</a>
    </div>
</div>

<script>
    var loginModal = document.getElementById("myModal");
    var registerModal = document.getElementById("registerModal");
    var span = document.getElementsByClassName("close");

    document.getElementById("login-link").addEventListener('click', function() {
        loginModal.style.display = "block";
        document.getElementById("original-login-text").style.display = "block"; // Show original login text
        document.getElementById("original-register-text").style.display = "none"; // Hide register text
    });

    document.getElementById("register-link").addEventListener('click', function() {
        registerModal.style.display = "block"; // Show registration modal
        document.getElementById("original-register-text").style.display = "block"; // Show original register text
        document.getElementById("original-login-text").style.display = "none"; // Hide login text
    });

    for (var i = 0; i < span.length; i++) {
        span[i].onclick = function() {
            loginModal.style.display = "none";
            registerModal.style.display = "none"; // Close both modals
            document.getElementById("original-login-text").style.display = "none"; // Hide login text
            document.getElementById("original-register-text").style.display = "none"; // Hide register text
        }
    }

    window.onclick = function(event) {
        if (event.target == loginModal) {
            loginModal.style.display = "none";
            document.getElementById("original-login-text").style.display = "none"; // Hide login text
        } else if (event.target == registerModal) {
            registerModal.style.display = "none";
            document.getElementById("original-register-text").style.display = "none"; // Hide register text
        }
    }
</script>

</body>
</html>
