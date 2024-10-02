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
            overflow: hidden; /* Prevent scrollbars from appearing */
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
        canvas {
            position: absolute;
            top: 0;
            left: 0;
            pointer-events: none; /* Allow clicks to pass through to the form */
        }
    </style>
</head>
<body>
    <canvas id="fireworksCanvas"></canvas>

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
            }, 6000); // Adjust time as needed
        });

        const canvas = document.getElementById('fireworksCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const fireworks = [];

        // Create a firework at the specified position
        function createFirework(x, y) {
            const firework = {
                x: x,
                y: y,
                particles: [],
                explode: false,
            };
            fireworks.push(firework);
        }

        // Create fewer particles (using the star emoji) for the firework explosion
        function createParticles(x, y) {
            const colors = ['#FF5733', '#FFBD33', '#DBFF33', '#75FF33', '#33FF57', '#33FFBD', '#33DBFF', '#3375FF', '#3357FF', '#5733FF'];

            for (let i = 0; i < 50; i++) { // Reduced the number of particles
                const angle = Math.random() * Math.PI * 2;
                const particle = {
                    x: x,
                    y: y,
                    speedX: Math.cos(angle) * (Math.random() * 6 + 2),
                    speedY: Math.sin(angle) * (Math.random() * 6 + 2),
                    color: colors[Math.floor(Math.random() * colors.length)],
                    lifespan: Math.random() * 40 + 30,
                };
                fireworks[fireworks.length - 1].particles.push(particle);
            }
        }

        function updateParticles() {
            fireworks.forEach((firework, index) => {
                if (!firework.explode) {
                    createParticles(firework.x, firework.y);
                    firework.explode = true; // Set to true after explosion
                }
                firework.particles.forEach((particle, particleIndex) => {
                    particle.x += particle.speedX; // Update position
                    particle.y += particle.speedY; // Update position
                    particle.speedY += 0.05; // Gravity effect
                    particle.lifespan -= 1; // Decrease lifespan

                    if (particle.lifespan <= 0) {
                        firework.particles.splice(particleIndex, 1); // Remove particle if lifespan ends
                    }
                });
                if (firework.particles.length === 0) {
                    fireworks.splice(index, 1); // Remove firework if no particles left
                }
            });
        }

        function drawParticles() {
            fireworks.forEach(firework => {
                firework.particles.forEach(particle => {
                    ctx.fillStyle = particle.color; // Set color
                    ctx.font = '24px Arial';
                    ctx.fillText('🌟', particle.x, particle.y); // Draw star
                });
            });
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height); // Clear canvas
            drawParticles(); // Draw particles
            updateParticles(); // Update particles
            requestAnimationFrame(animate); // Loop the animation
        }

        // Trigger fireworks at intervals
        setInterval(() => {
            const x = Math.random() * canvas.width;
            const y = Math.random() * canvas.height;
            createFirework(x, y);
        }, 1000); // Adjust interval for firework creation

        // Start the animation loop
        animate();
    </script>
</body>
</html>
