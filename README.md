<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shared Diaries 2026</title>
    <!-- EmailJS Script -->
    <script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
    <script>
        (function() {
            emailjs.init("eYvRww5Z7KHJ30qBu"); // Your Public Key
        })();
    </script>
    <style>
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            text-align: center;
            background: linear-gradient(45deg, #ff9a9e, #fecfef, #a8edea, #fed6e3, #d299c2);
            background-size: 400% 400%;
            animation: gradientShift 10s ease infinite;
            padding: 20px;
            overflow: hidden;
            position: relative;
        }
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        .container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-bottom: 40px;
        }
        .diary {
            background: rgba(255, 255, 255, 0.8);
            border-radius: 15px;
            padding: 20px;
            width: 45%;
            min-width: 300px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        .diary h2 {
            color: #333;
            margin-bottom: 10px;
        }
        textarea {
            width: 100%;
            height: 200px;
            border: 2px solid #ff6b6b;
            border-radius: 10px;
            padding: 10px;
            font-size: 16px;
            resize: vertical;
        }
        button {
            font-size: 16px;
            padding: 10px 20px;
            margin: 10px;
            cursor: pointer;
            border: none;
            border-radius: 25px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        .save-btn {
            background: linear-gradient(45deg, #ff6b6b, #feca57);
            color: white;
        }
        .save-btn:hover {
            transform: scale(1.05);
        }
        /* Floating flowers */
        .flower {
            position: absolute;
            font-size: 24px;
            animation: float 15s linear infinite;
            pointer-events: none;
        }
        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-100px) rotate(360deg); opacity: 0; }
        }
        .flower:nth-child(1) { left: 10%; animation-delay: 0s; }
        .flower:nth-child(2) { left: 20%; animation-delay: 2s; }
        .flower:nth-child(3) { left: 30%; animation-delay: 4s; }
        .flower:nth-child(4) { left: 40%; animation-delay: 6s; }
        .flower:nth-child(5) { left: 50%; animation-delay: 8s; }
        .flower:nth-child(6) { left: 60%; animation-delay: 10s; }
        .flower:nth-child(7) { left: 70%; animation-delay: 12s; }
        .flower:nth-child(8) { left: 80%; animation-delay: 14s; }
    </style>
</head>
<body>
    <!-- Floating flowers -->
    <div class="flower">🌸</div>
    <div class="flower">🌺</div>
    <div class="flower">🌻</div>
    <div class="flower">🌷</div>
    <div class="flower">🌹</div>
    <div class="flower">🌼</div>
    <div class="flower">🌻</div>
    <div class="flower">🌸</div>

    <h1>Shared Diaries 2026 👸💕</h1>
    <div class="container">
        <div class="diary">
            <h2>Prince Diary</h2>
            <textarea id="prince-notes" placeholder="Write your notes here..."></textarea>
            <button class="save-btn" onclick="saveNotes('prince')">Save to 2026 Diary</button>
        </div>
        <div class="diary">
            <h2>Gutu Diary</h2>
            <textarea id="gutu-notes" placeholder="Write your notes here..."></textarea>
            <button class="save-btn" onclick="saveNotes('gutu')">Save to 2026 Diary</button>
        </div>
    </div>

    <script>
        // Save notes function with email sending (no localStorage)
        function saveNotes(diary) {
            const notes = document.getElementById(diary + '-notes').value;
            
            // Send email via EmailJS
            const templateParams = {
                diary: diary.charAt(0).toUpperCase() + diary.slice(1), // Capitalize (e.g., Prince)
                notes: notes,
                date: new Date().toLocaleString()
            };
            
            emailjs.send('service_08qen3h', 'template_faoh539', templateParams) // Your Service ID and Template ID
                .then(function(response) {
                    alert('Notes emailed! 📧');
                }, function(error) {
                    alert('Email failed. Check console for details.');
                    console.log('EmailJS error:', error);
                });
        }
    </script>
</body>
</html>
