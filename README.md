<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Unauthorized Access - Just for You</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Courier New', monospace;
            background: linear-gradient(135deg, #1a1a2e 0%, #0f3460 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .container {
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .slide {
            width: 95%;
            max-width: 500px;
            background: rgba(0, 0, 0, 0.8);
            border: 2px solid #00ff41;
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 0 20px rgba(0, 255, 65, 0.5), inset 0 0 20px rgba(0, 255, 65, 0.1);
            animation: glitch 2s infinite;
            display: none;
        }

        .slide.active {
            display: block;
        }

        @keyframes glitch {
            0%, 100% {
                text-shadow: 0 0 10px rgba(0, 255, 65, 0.5);
            }
            50% {
                text-shadow: 0 0 20px rgba(0, 255, 65, 0.8);
            }
        }

        .photo-container {
            margin: 15px 0;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 0 20px rgba(255, 105, 180, 0.5);
            border: 2px solid #ff69b4;
        }

        .photo-container img {
            width: 100%;
            height: auto;
            max-height: 250px;
            object-fit: cover;
            display: block;
        }

        .header {
            color: #00ff41;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .header::before {
            content: "⚠️ ";
            margin-right: 10px;
        }

        .quiz-title {
            color: #00ff41;
            font-size: 18px;
            margin-bottom: 20px;
            font-weight: bold;
            text-transform: uppercase;
        }

        .quiz-question {
            color: #00ff41;
            font-size: 16px;
            margin: 20px 0;
            font-weight: bold;
        }

        .quiz-options {
            margin: 20px 0;
        }

        .btn-quiz {
            padding: 14px 25px;
            font-size: 14px;
            border: 2px solid #00ff41;
            background: transparent;
            color: #00ff41;
            border-radius: 5px;
            cursor: pointer;
            font-family: 'Courier New', monospace;
            font-weight: bold;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            width: 100%;
            margin: 10px 0;
            text-align: left;
            padding: 15px;
        }

        .btn-quiz:hover {
            background: rgba(0, 255, 65, 0.2);
            box-shadow: 0 0 15px rgba(0, 255, 65, 0.6);
        }

        .btn-quiz.correct {
            border-color: #00ff41;
            box-shadow: 0 0 15px rgba(0, 255, 65, 1);
        }

        .btn-quiz.wrong {
            border-color: #ff6b6b;
            box-shadow: 0 0 15px rgba(255, 107, 107, 1);
        }

        .feedback {
            color: #ff69b4;
            font-size: 16px;
            margin: 20px 0;
            font-weight: bold;
            font-style: italic;
        }

        .error-screen {
            color: #ff6b6b;
            font-size: 20px;
            margin: 20px 0;
            font-weight: bold;
            text-transform: uppercase;
            animation: pulse 0.5s infinite;
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.7;
            }
        }

        .message {
            color: #00ff41;
            font-size: 15px;
            line-height: 1.6;
            text-align: left;
            margin: 20px 0;
            white-space: pre-wrap;
            word-wrap: break-word;
            animation: typing 2s steps(60, end);
        }

        @keyframes typing {
            from {
                opacity: 0.7;
            }
            to {
                opacity: 1;
            }
        }

        .heart {
            color: #ff69b4;
            font-size: 20px;
            margin: 0 5px;
        }

        .button-container {
            margin-top: 25px;
            display: flex;
            gap: 12px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 14px 25px;
            font-size: 15px;
            border: 2px solid #00ff41;
            background: transparent;
            color: #00ff41;
            border-radius: 5px;
            cursor: pointer;
            font-family: 'Courier New', monospace;
            font-weight: bold;
            text-transform: uppercase;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            min-width: 140px;
        }

        .btn-quiz {
            padding: 14px 25px;
            font-size: 14px;
            border: 2px solid #00ff41;
            background: transparent;
            color: #00ff41;
            border-radius: 5px;
            cursor: pointer;
            font-family: 'Courier New', monospace;
            font-weight: bold;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            width: 100%;
            margin: 10px 0;
            text-align: left;
            padding: 15px;
        }

        .btn-quiz:hover {
            background: rgba(0, 255, 65, 0.2);
            box-shadow: 0 0 15px rgba(0, 255, 65, 0.6);
        }

        .btn-quiz.correct {
            border-color: #00ff41;
            box-shadow: 0 0 15px rgba(0, 255, 65, 1);
        }

        .btn-quiz.wrong {
            border-color: #ff6b6b;
            box-shadow: 0 0 15px rgba(255, 107, 107, 1);
        }

        .quiz-title {
            color: #00ff41;
            font-size: 18px;
            margin-bottom: 20px;
            font-weight: bold;
            text-transform: uppercase;
        }

        .quiz-question {
            color: #00ff41;
            font-size: 16px;
            margin: 20px 0;
            font-weight: bold;
        }

        .quiz-options {
            margin: 20px 0;
        }

        .feedback {
            color: #ff69b4;
            font-size: 16px;
            margin: 20px 0;
            font-weight: bold;
            font-style: italic;
        }

        .error-screen {
            color: #ff6b6b;
            font-size: 20px;
            margin: 20px 0;
            font-weight: bold;
            text-transform: uppercase;
            animation: pulse 0.5s infinite;
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.7;
            }
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: #00ff41;
            transition: left 0.3s ease;
            z-index: -1;
        }

        .btn:hover::before {
            left: 0;
        }

        .btn:hover {
            color: #1a1a2e;
            box-shadow: 0 0 20px rgba(0, 255, 65, 0.8);
        }

        .btn-yes {
            border-color: #ff69b4;
        }

        .btn-yes::before {
            background: #ff69b4;
        }

        .btn-yes:hover {
            color: #1a1a2e;
            box-shadow: 0 0 20px rgba(255, 105, 180, 0.8);
        }

        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            animation: twinkle 3s infinite;
        }

        @keyframes twinkle {
            0%, 100% {
                opacity: 0.3;
            }
            50% {
                opacity: 1;
            }
        }

        @media (max-width: 600px) {
            .slide {
                padding: 15px;
            }

            .header {
                font-size: 16px;
            }

            .message {
                font-size: 14px;
                line-height: 1.5;
            }

            .button-container {
                flex-direction: column;
                gap: 10px;
            }

            .btn {
                width: 100%;
                padding: 16px 20px;
                font-size: 16px;
            }

            .photo-container img {
                max-height: 200px;
            }
        }
    </style>
</head>
<body>
    <div class="stars" id="starfield"></div>

    <div class="container">
        <div class="slide active" id="slide1">
            <div class="header">⚠️ Unauthorized Access Detected</div>
            
            <div class="photo-container">
                <img src="IMG_9544.jpeg" alt="Who are you?" id="couplePhoto">
            </div>

            <div class="message">Wait... who are you?

If my developer, Chris, finds out you're here, 
he'll probably wipe me off the internet.

Unless u can prove who you are.
Ready to answer a few questions? <span class="heart">💕</span></div>

            <div class="button-container">
                <button class="btn btn-yes" onclick="startQuiz()">Yes, I'm Ready! 💪</button>
                <button class="btn" onclick="denied()">No, I'm Out... 😢</button>
            </div>
        </div>

        <!-- Quiz Introduction -->
        <div class="slide" id="quizIntro">
            <div class="quiz-title">⚡ IDENTIFICATION TEST ⚡</div>
            <div class="message" style="margin: 30px 0; font-size: 16px;">
this is a identify test...

you have to answer CORRECTLY 
to all the questions you see,

otherwise 

AMCHI AMCHI YAL ARGEN!!!!</div>
            <button class="btn btn-yes" onclick="nextSlide('q1')">Start Test 🔥</button>
        </div>

        <!-- Question 1 -->
        <div class="slide" id="q1">
            <div class="quiz-title">Question 1/5</div>
            <div class="quiz-question">What's my Developer's favorite activity?</div>
            <div class="quiz-options">
                <button class="btn-quiz" onclick="checkAnswer('q1', 0, false, 'Wrong answer!')">1. Eating nduja</button>
                <button class="btn-quiz" onclick="checkAnswer('q1', 1, false, 'Wrong answer!')">2. Invading Mozambique</button>
                <button class="btn-quiz" onclick="checkAnswer('q1', 2, true, 'yes, u are only lucky...')">3. Pooping all the time</button>
            </div>
        </div>

        <!-- Question 2 -->
        <div class="slide" id="q2">
            <div class="quiz-title">Question 2/5</div>
            <div class="quiz-question">What's the name of the plushie my Developer gave to his woman?</div>
            <div class="quiz-options">
                <button class="btn-quiz" onclick="checkAnswer('q2', 0, false, 'Wrong answer!')">1. Muhammar Gheddafi</button>
                <button class="btn-quiz" onclick="checkAnswer('q2', 1, true, 'okay u are scaring me... but let\'s go ahead.')">2. Mushroom il Fungo</button>
                <button class="btn-quiz" onclick="checkAnswer('q2', 2, false, 'Wrong answer!')">3. Rohou hawlouha/Rani mtwahchha</button>
            </div>
        </div>

        <!-- Question 3 -->
        <div class="slide" id="q3">
            <div class="quiz-title">Question 3/5</div>
            <div class="quiz-question">What's the nickname my Developer's woman gave to him?</div>
            <div class="quiz-options">
                <button class="btn-quiz" onclick="checkAnswer('q3', 0, false, 'Wrong answer!')">1. Abdelmajid Tabboune</button>
                <button class="btn-quiz" onclick="checkAnswer('q3', 1, false, 'Wrong answer!')">2. ORGEN</button>
                <button class="btn-quiz" onclick="checkAnswer('q3', 2, true, 'ehm... WHO ARE YOUUUUU??? YA YEMMA')">3. Charchori</button>
            </div>
        </div>

        <!-- Question 4 -->
        <div class="slide" id="q4">
            <div class="quiz-title">Question 4/5</div>
            <div class="quiz-question">What's the name of the ghost inside my Developer's woman house?</div>
            <div class="quiz-options">
                <button class="btn-quiz" onclick="checkAnswer('q4', 0, false, 'Nope, they were in the past house')">1. Wissal and Nesrine</button>
                <button class="btn-quiz" onclick="checkAnswer('q4', 1, false, 'Wrong answer!')">2. Hibatallah Aya Malak</button>
                <button class="btn-quiz" onclick="checkAnswer('q4', 2, true, 'DID U STUDY HIBACHRISSOLOGY AT SCHOOL???')">3. Ruqaya</button>
            </div>
        </div>

        <!-- Question 5 -->
        <div class="slide" id="q5">
            <div class="quiz-title">Question 5/5</div>
            <div class="quiz-question">Why my Developer's woman should win Oscar Award for best actress?</div>
            <div class="quiz-options">
                <button class="btn-quiz" onclick="checkAnswer('q5', 0, false, 'Wrong answer!')">1. She ate bengali pizza acting it was good</button>
                <button class="btn-quiz" onclick="checkAnswer('q5', 1, true, 'ur name starts with H??? NO WAY I\'M SPEECHLESS')">2. She saved her man dignity when he has a cannonball in his A$$</button>
                <button class="btn-quiz" onclick="checkAnswer('q5', 2, false, 'Wrong answer!')">3. She is Algerina Jolie</button>
            </div>
        </div>

        <!-- Error Screen -->
        <div class="slide" id="errorScreen">
            <div class="error-screen">🚨 AMCHI AMCHI YAL HARRAGA 🚨</div>
            <div class="error-screen">MY DEVELOPER WILL FIND YOU!!!</div>
            <button class="btn btn-yes" onclick="showRetryScreen()" style="margin-top: 30px;">Next...</button>
        </div>

        <!-- Retry Screen -->
        <div class="slide" id="retryScreen">
            <div class="quiz-question" style="color: #ff69b4; margin-top: 50px;">Okay u have another chance to convince me...</div>
            <button class="btn btn-yes" onclick="goToPreviousQuestion()" style="margin-top: 40px;">Try Again 💪</button>
        </div>

        <!-- Success Screen -->
        <div class="slide" id="successScreen">
            <div class="quiz-title">🎉 ALL CORRECT! 🎉</div>
            <div class="message" style="margin: 30px 0; font-size: 16px; color: #ff69b4;">
YOU DID IT!!!

WELCOME BACK HOME LOVE 💕

I KNEW IT WAS YOU...</div>
            <button class="btn btn-yes" onclick="showFinal()">Continue 💘</button>
        </div>

        <!-- Final Screen -->
        <div class="slide" id="finalScreen">
            <div class="quiz-title">✨ Welcome Home ✨</div>
            <div class="message" style="margin: 30px 0; font-size: 16px; color: #ff69b4;">
This website is dedicated to you.
Because you are the best thing that ever happened to me.

Happy to have you here 💕</div>
        </div>
    </div>

    <script>
        let currentQuestion = null;
        let quizStarted = false;

        // Create starfield background
        function createStars() {
            const starfield = document.getElementById('starfield');
            for (let i = 0; i < 50; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.width = Math.random() * 3 + 'px';
                star.style.height = star.style.width;
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.animationDelay = Math.random() * 3 + 's';
                starfield.appendChild(star);
            }
        }

        function hideAllSlides() {
            const slides = document.querySelectorAll('.slide');
            slides.forEach(slide => slide.classList.remove('active'));
        }

        function showSlide(slideId) {
            hideAllSlides();
            document.getElementById(slideId).classList.add('active');
        }

        function nextSlide(slideId) {
            showSlide(slideId);
            currentQuestion = slideId;
            quizStarted = true;
        }

        function startQuiz() {
            showSlide('quizIntro');
        }

        function denied() {
            alert('😢 Oh no! Mi dispiacerà vedere che te ne vai...');
        }

        function checkAnswer(questionId, answerIndex, isCorrect, feedback) {
            if (isCorrect) {
                // Answer is correct
                showFeedback(questionId, feedback, true);
                setTimeout(() => {
                    const nextQuestion = getNextQuestion(questionId);
                    if (nextQuestion) {
                        showSlide(nextQuestion);
                        currentQuestion = nextQuestion;
                    } else {
                        showSlide('successScreen');
                    }
                }, 2000);
            } else {
                // Answer is wrong
                showErrorScreen(questionId, feedback);
            }
        }

        function showFeedback(questionId, feedback, isCorrect) {
            const slide = document.getElementById(questionId);
            const feedbackDiv = document.createElement('div');
            feedbackDiv.className = 'feedback';
            feedbackDiv.innerHTML = feedback;
            
            // Remove previous feedback if exists
            const oldFeedback = slide.querySelector('.feedback');
            if (oldFeedback) oldFeedback.remove();
            
            slide.appendChild(feedbackDiv);
        }

        function showErrorScreen(questionId, specificFeedback) {
            showSlide('errorScreen');
            currentQuestion = questionId;
        }

        function showRetryScreen() {
            showSlide('retryScreen');
        }

        function goToPreviousQuestion() {
            showSlide(currentQuestion);
            // Remove feedback
            const slide = document.getElementById(currentQuestion);
            const feedback = slide.querySelector('.feedback');
            if (feedback) feedback.remove();
        }

        function getNextQuestion(currentQuestion) {
            const questions = ['q1', 'q2', 'q3', 'q4', 'q5'];
            const currentIndex = questions.indexOf(currentQuestion);
            if (currentIndex < questions.length - 1) {
                return questions[currentIndex + 1];
            }
            return null;
        }

        function showFinal() {
            showSlide('finalScreen');
        }

        // Initialize
        window.addEventListener('load', () => {
            createStars();
            showSlide('slide1');
        });
    </script>
</body>
</html>
