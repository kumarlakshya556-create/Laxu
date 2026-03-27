<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Surprise</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Poppins:wght@300;400&display=swap" rel="stylesheet">
    <style>
        :root {
            --aesthetic-pink: #fce4ec;
            --dark-pink: #f06292;
            --accent-pink: #ec407a;
            --soft-white: #fff5f8;
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
            background-color: var(--aesthetic-pink);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            color: #4a4a4a;
        }

        .container {
            width: 90%;
            max-width: 400px;
            background: var(--soft-white);
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            text-align: center;
            transition: all 0.5s ease;
        }

        .page { display: none; animation: fadeIn 0.8s ease; }
        .active { display: block; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1, h2 { font-family: 'Dancing Script', cursive; color: var(--accent-pink); }
        
        input {
            width: 80%;
            padding: 12px;
            border: 2px solid var(--aesthetic-pink);
            border-radius: 25px;
            outline: none;
            margin-bottom: 20px;
            text-align: center;
        }

        .btn {
            background: var(--dark-pink);
            color: white;
            border: none;
            padding: 10px 25px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            transition: 0.3s;
            text-decoration: none;
            display: inline-block;
            margin-top: 10px;
        }

        .btn:hover { background: var(--accent-pink); transform: scale(1.05); }

        .back-btn {
            background: transparent;
            color: var(--dark-pink);
            border: 1px solid var(--dark-pink);
            margin-top: 20px;
        }

        .gift-container {
            display: flex;
            justify-content: space-around;
            margin: 20px 0;
        }

        .gift-box {
            font-size: 3rem;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .gift-box:hover { transform: scale(1.2); }

        .quote-text {
            font-size: 1.2rem;
            line-height: 1.6;
            font-style: italic;
        }

        .final-name {
            font-family: 'Dancing Script', cursive;
            font-size: 2.5rem;
            color: var(--accent-pink);
            display: block;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <div class="container">
        <div id="page1" class="page active">
            <h1>Hello Beautiful...</h1>
            <input type="text" id="userName" placeholder="Enter your name here">
            <br>
            <button class="btn" onclick="nextPage(2)">Next</button>
        </div>

        <div id="page2" class="page">
            <h2>Pick a Gift</h2>
            <div class="gift-container">
                <div class="gift-box" onclick="nextPage('gift1')">🎁</div>
                <div class="gift-box" onclick="nextPage('gift2')">🎁</div>
                <div class="gift-box" onclick="nextPage('gift3')">🎁</div>
            </div>
            <p style="font-size: 0.8rem; color: #999;">Click on a gift to open it</p>
            <button class="btn" onclick="nextPage(3)">Proceed to End</button>
        </div>

        <div id="gift1" class="page">
            <h2>A Note for You</h2>
            <p class="quote-text">"You are the kind of magic that makes the world feel like a better place just by being in it. Your smile is my favorite view."</p>
            <button class="btn back-btn" onclick="nextPage(2)">Go Back</button>
        </div>

        <div id="gift2" class="page">
            <h2>Shayari</h2>
            <p class="quote-text">"तुम तो चाँद हो, मेरे बगैर भी चमकोगे, मैं वो आसमान हूँ, जो तेरे बगैर बिल्कुल तन्हा हूँ ।"</p>
            <button class="btn back-btn" onclick="nextPage(2)">Go Back</button>
        </div>

        <div id="gift3" class="page">
            <h2>For You</h2>
            <p class="quote-text">"Are you a magician? Because whenever I look at you, everyone else disappears."</p>
            <button class="btn back-btn" onclick="nextPage(2)">Go Back</button>
        </div>

        <div id="page3" class="page">
            <h1>I Love You</h1>
            <span id="displayName" class="final-name"></span>
            <button class="btn back-btn" onclick="nextPage(1)">Restart</button>
        </div>
    </div>

    <script>
        function nextPage(pageId) {
            // Hide all pages
            const pages = document.querySelectorAll('.page');
            pages.forEach(p => p.classList.remove('active'));

            // Show target page
            let target;
            if (typeof pageId === 'number') {
                target = document.getElementById('page' + pageId);
            } else {
                target = document.getElementById(pageId);
            }
            
            target.classList.add('active');

            // Set name on final page
            if(pageId === 3) {
                const name = document.getElementById('userName').value;
                document.getElementById('displayName').innerText = name || "Sweetheart";
            }
        }
    </script>
</body>
</html>
