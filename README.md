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
        .grid-item {
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            text-align: center;
            cursor: pointer;
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
    </style>
</head>
<body>

<header>
    <h1>My Portfolio</h1>
    <nav>
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
    </nav>
</header>

<section id="about">
    <h2>About Me</h2>
    <p>Welcome to my portfolio. Here are some of my projects.</p>
</section>

<section id="projects">
    <h2>Projects</h2>
    <div class="grid-container">
        <div class="grid-item" data-title="Project 1" data-description="Description of Project 1.">
            <a href="https://drain1103.github.io/Htet/" target="_blank">
                <h3>Project 1</h3>
            </a>
        </div>
        <div class="grid-item" data-title="Project 2" data-description="Description of Project 2.">
            <h3>Project 2</h3>
        </div>
        <div class="grid-item" data-title="Project 3" data-description="Description of Project 3.">
            <h3>Project 3</h3>
        </div>
        <div class="grid-item" data-title="Project 4" data-description="Description of Project 4.">
            <h3>Project 4</h3>
        </div>
    </div>
</section>

<section id="contact">
    <h2>Contact Me</h2>
    <p>Email: example@example.com</p>
</section>

<div id="myModal" class="modal">
    <div class="modal-content">
        <span class="close">&times;</span>
        <h3 id="modalTitle"></h3>
        <p id="modalDescription"></p>
    </div>
</div>

<footer>
    <p>&copy; 2024 My Portfolio</p>
</footer>

<script>
    const modal = document.getElementById("myModal");
    const span = document.getElementsByClassName("close")[0];

    document.querySelectorAll('.grid-item').forEach(item => {
        item.addEventListener('click', function() {
            const title = this.getAttribute('data-title');
            const description = this.getAttribute('data-description');
            document.getElementById('modalTitle').innerText = title;
            document.getElementById('modalDescription').innerText = description;
            modal.style.display = "block";
        });
    });

    span.onclick = function() {
        modal.style.display = "none";
    }

    window.onclick = function(event) {
        if (event.target === modal) {
            modal.style.display = "none";
        }
    }
</script>

</body>
</html>
