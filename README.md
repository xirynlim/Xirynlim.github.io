# Xirynlim.github.io
CMNS2016_Ass1_Website
[CMNS2016_Ass1_video website.index.html](https://github.com/user-attachments/files/28837525/CMNS2016_Ass1_video.website.index.html)
<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Video Player</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-color: #1a1a1a;
            color: white;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 30px 20px;
        }


        .container {
            width: 100%;
            max-width: 900px;
            background: #2d2d2d;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 0 20px rgba(0,0,0,0.3);
        }

        .title {
    text-align: center;
    margin-bottom: 25px;
    font-size: 28px;
    color: #ff0000;
}

        .video-section {
            position: relative;
            width: 100%;
            margin-bottom: 20px;
        }

      video {
    width: 60%;
    max-width: 500px;
    height: auto;
    display: block;
    margin: 0 auto;
    border-radius: 8px;
}

        .choice-buttons {

            display: none;
            gap: 20px;
            justify-content: center;
            margin: 30px 0;
            flex-wrap: wrap;
        }



        .choice-btn {

            padding: 14px 30px;
            font-size: 18px;
            border: none;
            border-radius: 8px;
            background: red;
            color: white;
            cursor: pointer;
            transition: 0.3s;
            min-width: 160px;
        }

        .choice-btn:hover {
            background: #0056b3;
            transform: scale(1.05);
        }

        .like-section {
            display: flex;
            align-items: center;
            gap: 15px;
            justify-content: center;
            margin-top: 20px;
        }

        .like-btn {
            padding: 10px 20px;
            font-size: 16px;
            border: none;
            border-radius: 6px;
            background: #28a745;
            color: white;
            cursor: pointer;
            transition: 0.3s;
        }

        .like-btn:hover {
            background: #1e7e34;
        }

        .like-count {
            font-size: 18px;
            font-weight: bold;
        }

        .hidden {
            display: none !important;
        }

        .back-btn {
            padding: 12px 25px;
            background: #dc3545;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            margin: 20px auto;
            display: block;
            font-size: 16px;
        }

        .back-btn:hover {
            background: #b02a37;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="title">Don't Open the Door</h1>

        <!-- Main Video 1 (Default Display) -->
        <div id="mainVideoSection" class="video-section">
            <video id="mainVideo" controls>
                <source src="https://youtube.com/shorts/BEWkeGrSfVI?si=ms3WH9gKsN0XH4fo">
                Your browser does not support video playback.
            </video>
        </div>

        <!-- Choice Buttons -->
        <div id="choiceButtons" class="choice-buttons">
            <button class="choice-btn" onclick="playVideo1()">Zombie???</button>
            <button class="choice-btn" onclick="playVideo2()">Who is there?</button>
        </div>

        <!-- Result Video 1 -->
        <div id="resultVideo1Section" class="video-section hidden">
            <video id="resultVideo1" controls>
                <source src="https://youtube.com/shorts/4e3PuV0hqzc?feature=share">
                Your browser does not support video playback.
            </video>
            <button class="back-btn" onclick="goBackToMain()">Back to Main Video</button>
        </div>

        <!-- Result Video 2 -->
        <div id="resultVideo2Section" class="video-section hidden">
            <video id="resultVideo2" controls>
                <source src="https://youtube.com/shorts/X6lOkHuSuMQ?feature=share">
                Your browser does not support video playback.
            </video>
            <button class="back-btn" onclick="goBackToMain()">Back to Main Video</button>
        </div>

        <!-- Like Interaction -->
        <div class="like-section">
            <button id="likeBtn" class="like-btn">Like This Video</button>
            <span class="like-count">Likes: <span id="likeCount">0</span></span>
        </div>
    </div>

    <script>
        // Like function
        let likeCount = 0;
        const likeBtn = document.getElementById('likeBtn');
        const likeCountDisplay = document.getElementById('likeCount');

        likeBtn.addEventListener('click', () => {
            likeCount++;
            likeCountDisplay.textContent = likeCount;
            likeBtn.textContent = "Liked ✓";
            likeBtn.style.background = "#1e7e34";
        });

        // Video switch functions
        function playVideo1() {
            document.getElementById('mainVideoSection').classList.add('hidden');
            document.getElementById('choiceButtons').classList.add('hidden');
            document.getElementById('resultVideo1Section').classList.remove('hidden');
            document.getElementById('resultVideo1').play();
        }

        function playVideo2() {
            document.getElementById('mainVideoSection').classList.add('hidden');
            document.getElementById('choiceButtons').classList.add('hidden');
            document.getElementById('resultVideo2Section').classList.remove('hidden');
            document.getElementById('resultVideo2').play();
        }

        function goBackToMain() {
            // Hide all result videos
            document.getElementById('resultVideo1Section').classList.add('hidden');
            document.getElementById('resultVideo2Section').classList.add('hidden');
            
            // Show main video and choices
            document.getElementById('mainVideoSection').classList.remove('hidden');
            document.getElementById('choiceButtons').classList.remove('hidden');
            
            // Pause all videos
            document.getElementById('mainVideo').pause();
            document.getElementById('resultVideo1').pause();
            document.getElementById('resultVideo2').pause();
        }


const mainVideo = document.getElementById('mainVideo');
const choiceButtons = document.getElementById('choiceButtons');

// 视频播放结束后显示按钮
mainVideo.addEventListener('ended', () => {
    choiceButtons.style.display = 'flex';
});

    </script>
</body>
</html>
