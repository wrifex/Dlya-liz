# Dlya-liz
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Важный вопрос 💌</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/twemoji/14.0.2/twemoji.min.js" crossorigin="anonymous"></script>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Nunito:wght@400;600;700&display=swap');

  /* Twemoji images */
  img.emoji {
    height: 1.2em;
    width: 1.2em;
    vertical-align: -0.15em;
    display: inline-block;
  }
  .card-emoji img.emoji {
    height: 1em;
    width: 1em;
    vertical-align: middle;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    min-height: 100vh;
    background: linear-gradient(135deg, #ffe4f0 0%, #ffd6e8 40%, #fce4ec 100%);
    font-family: 'Nunito', sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    position: relative;
  }

  /* Floating hearts background */
  .hearts-bg {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 0;
  }

  .heart-float {
    position: absolute;
    font-size: 1.5rem;
    animation: floatUp linear infinite;
    opacity: 0.4;
  }

  @keyframes floatUp {
    0% { transform: translateY(110vh) rotate(0deg); opacity: 0.4; }
    100% { transform: translateY(-10vh) rotate(20deg); opacity: 0; }
  }

  /* Card */
  .card {
    position: relative;
    z-index: 10;
    background: rgba(255,255,255,0.85);
    backdrop-filter: blur(12px);
    border-radius: 28px;
    padding: 48px 52px;
    max-width: 480px;
    width: 90%;
    text-align: center;
    box-shadow: 0 20px 60px rgba(233, 30, 99, 0.15), 0 4px 16px rgba(0,0,0,0.06);
    border: 1.5px solid rgba(255, 182, 193, 0.5);
  }

  .card-emoji {
    font-size: 3.5rem;
    margin-bottom: 16px;
    display: block;
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.12); }
  }

  .card h1 {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    color: #c2185b;
    margin-bottom: 8px;
    line-height: 1.25;
  }

  .card p.sub {
    color: #999;
    font-size: 0.9rem;
    margin-bottom: 36px;
  }

  /* Buttons */
  .btn-row {
    display: flex;
    gap: 20px;
    justify-content: center;
    align-items: center;
  }

  .btn-yes {
    background: linear-gradient(135deg, #e91e63, #f06292);
    color: white;
    border: none;
    padding: 16px 42px;
    font-size: 1.15rem;
    font-family: 'Nunito', sans-serif;
    font-weight: 700;
    border-radius: 50px;
    cursor: pointer;
    transition: transform 0.15s, box-shadow 0.15s;
    box-shadow: 0 6px 20px rgba(233,30,99,0.35);
  }

  .btn-yes:hover {
    transform: scale(1.06);
    box-shadow: 0 10px 28px rgba(233,30,99,0.45);
  }

  .btn-no {
    background: #f5f5f5;
    color: #bbb;
    border: 2px solid #e0e0e0;
    padding: 16px 42px;
    font-size: 1.15rem;
    font-family: 'Nunito', sans-serif;
    font-weight: 700;
    border-radius: 50px;
    cursor: pointer;
    transition: transform 0.08s;
    position: relative;
  }

  /* Screen sections */
  .screen { display: none; }
  .screen.active { display: block; }

  /* Yes screen */
  #screen-yes h1 {
    font-family: 'Playfair Display', serif;
    font-size: 1.75rem;
    color: #c2185b;
    margin: 16px 0 8px;
    line-height: 1.3;
  }

  #screen-yes p {
    color: #888;
    font-size: 0.95rem;
    margin-bottom: 28px;
  }

  .next-btn {
    background: linear-gradient(135deg, #e91e63, #f06292);
    color: white;
    border: none;
    padding: 13px 36px;
    font-size: 1rem;
    font-family: 'Nunito', sans-serif;
    font-weight: 700;
    border-radius: 50px;
    cursor: pointer;
    box-shadow: 0 6px 18px rgba(233,30,99,0.3);
    transition: transform 0.15s;
  }
  .next-btn:hover { transform: scale(1.05); }

  /* Quiz */
  .quiz-question {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    color: #ad1457;
    margin-bottom: 24px;
    line-height: 1.35;
  }

  .quiz-options {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .quiz-opt {
    background: #fff0f5;
    border: 2px solid #f8bbd0;
    color: #c2185b;
    padding: 13px 20px;
    border-radius: 14px;
    cursor: pointer;
    font-size: 1rem;
    font-family: 'Nunito', sans-serif;
    font-weight: 600;
    text-align: left;
    transition: background 0.15s, border-color 0.15s, transform 0.1s;
  }

  .quiz-opt:hover {
    background: #fce4ec;
    border-color: #f48fb1;
    transform: translateX(4px);
  }

  /* Progress */
  .progress-bar {
    width: 100%;
    height: 5px;
    background: #fce4ec;
    border-radius: 99px;
    margin-bottom: 28px;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #e91e63, #f48fb1);
    border-radius: 99px;
    transition: width 0.4s ease;
  }

  /* Final screen */
  #screen-final h1 {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    color: #c2185b;
    margin: 16px 0 12px;
    line-height: 1.3;
  }

  #screen-final .punchline {
    font-size: 1rem;
    color: #888;
    margin-bottom: 10px;
    font-style: italic;
  }

  .restart-btn {
    background: none;
    border: 2px solid #f8bbd0;
    color: #e91e63;
    padding: 10px 28px;
    font-size: 0.9rem;
    font-family: 'Nunito', sans-serif;
    font-weight: 700;
    border-radius: 50px;
    cursor: pointer;
    margin-top: 20px;
    transition: background 0.15s;
  }
  .restart-btn:hover { background: #fce4ec; }

  /* Confetti burst */
  .confetti-burst {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 999;
  }
  .conf {
    position: absolute;
    width: 10px; height: 10px;
    border-radius: 2px;
    animation: confettiFall 1.8s ease-in forwards;
    opacity: 0;
  }
  @keyframes confettiFall {
    0% { transform: translateY(-20px) rotate(0deg); opacity: 1; }
    100% { transform: translateY(110vh) rotate(720deg); opacity: 0; }
  }

  /* Tooltip for No button */
  .no-wrapper { position: relative; display: inline-block; }
  .no-tooltip {
    position: absolute;
    bottom: 120%;
    left: 50%;
    transform: translateX(-50%);
    background: #333;
    color: white;
    padding: 6px 14px;
    border-radius: 8px;
    font-size: 0.8rem;
    white-space: nowrap;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.2s;
  }
  .no-wrapper:hover .no-tooltip {
    opacity: 1;
  }
</style>
</head>
<body>

<!-- Floating hearts -->
<div class="hearts-bg" id="heartsContainer"></div>

<div class="card">

  <!-- SCREEN 1: Main question -->
  <div class="screen active" id="screen-main">
    <span class="card-emoji">💌</span>
    <h1>Будешь моей девушкой?</h1>
    <p class="sub">Это самый важный вопрос в моей жизни ✨</p>
    <div class="btn-row">
      <button class="btn-yes" onclick="goYes()">Да 💕</button>
      <div class="no-wrapper">
        <div class="no-tooltip">Эта кнопка не для тебя 😏</div>
        <button class="btn-no" id="noBtn" onmouseover="runAway(this)" ontouchstart="runAway(this)">Нет</button>
      </div>
    </div>
  </div>

  <!-- SCREEN 2: Yes reaction -->
  <div class="screen" id="screen-yes">
    <span class="card-emoji">🥹🎉💗</span>
    <h1>Неужели ты выбрала «Да»?!</h1>
    <p>Я не могу поверить своему счастью… 🌸<br>Теперь мне нужно кое-что узнать о тебе!</p>
    <button class="next-btn" onclick="startQuiz()">Продолжить 💫</button>
  </div>

  <!-- SCREEN 3: Quiz -->
  <div class="screen" id="screen-quiz">
    <div class="progress-bar">
      <div class="progress-fill" id="progressFill" style="width:0%"></div>
    </div>
    <div class="quiz-question" id="quizQuestion"></div>
    <div class="quiz-options" id="quizOptions"></div>
  </div>

  <!-- SCREEN 4: Final prank -->
  <div class="screen" id="screen-final">
    <span class="card-emoji">😂</span>
    <h1>Ладно, это была шутка.</h1>
    <p class="punchline">Я просто хотел потратить твоё время 🫠</p>
    <p style="color:#ccc; font-size:0.85rem;">Надеюсь, было не слишком скучно 😅</p>
    <button class="restart-btn" onclick="restart()">Пройти ещё раз 🔁</button>
  </div>

</div>

<!-- Confetti container -->
<div class="confetti-burst" id="confettiBurst"></div>

<script>
  // === Twemoji — Apple-style emoji everywhere ===
  function parseEmoji() {
    twemoji.parse(document.body, {
      folder: 'svg',
      ext: '.svg',
      base: 'https://cdnjs.cloudflare.com/ajax/libs/twemoji/14.0.2/'
    });
  }
  document.addEventListener('DOMContentLoaded', parseEmoji);

  // === Floating hearts ===
  const container = document.getElementById('heartsContainer');
  const heartEmojis = ['❤️','💕','💗','💖','🌸','✨','💝'];
  for (let i = 0; i < 18; i++) {
    const h = document.createElement('div');
    h.className = 'heart-float';
    h.textContent = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];
    h.style.left = Math.random() * 100 + 'vw';
    h.style.fontSize = (1 + Math.random() * 1.5) + 'rem';
    h.style.animationDuration = (6 + Math.random() * 8) + 's';
    h.style.animationDelay = (Math.random() * 8) + 's';
    container.appendChild(h);
  }

  // === Run-away No button ===
  function runAway(btn) {
    const card = document.querySelector('.card');
    const cardRect = card.getBoundingClientRect();
    const btnRect = btn.getBoundingClientRect();

    const padding = 60;
    const maxX = cardRect.width - btnRect.width - padding;
    const maxY = cardRect.height - btnRect.height - padding;

    const randomX = Math.random() * maxX - maxX / 2;
    const randomY = Math.random() * maxY - maxY / 2;

    btn.style.position = 'relative';
    btn.style.left = randomX + 'px';
    btn.style.top = randomY + 'px';
    btn.style.transition = 'left 0.2s, top 0.2s';
  }

  // === Screen transitions ===
  function showScreen(id) {
    document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    setTimeout(parseEmoji, 10);
  }

  function goYes() {
    launchConfetti();
    showScreen('screen-yes');
  }

  // === Quiz ===
  const questions = [
    {
      q: "Ты больше любишь...",
      opts: ["☀️ Лето и море", "❄️ Зиму и снег", "🍂 Осень и уют", "🌸 Весну и цветы"]
    },
    {
      q: "Идеальный вечер — это...",
      opts: ["🎬 Фильм и плед", "🎉 Вечеринка с друзьями", "🍕 Вкусная еда дома", "🌃 Прогулка ночью"]
    },
    {
      q: "Какой ты котик?",
      opts: ["😺 Ласковый и добрый", "😼 Своенравный и гордый", "🙀 Вечно удивлённый", "😻 Влюблённый во всё"]
    },
    {
      q: "Твой любимый способ получать любовь?",
      opts: ["🤗 Обнимашки", "💬 Приятные слова", "🎁 Подарки-сюрпризы", "🕐 Время вдвоём"]
    }
  ];

  let currentQ = 0;

  function startQuiz() {
    currentQ = 0;
    showScreen('screen-quiz');
    renderQuestion();
  }

  function renderQuestion() {
    const q = questions[currentQ];
    document.getElementById('quizQuestion').textContent = q.q;
    document.getElementById('progressFill').style.width = (currentQ / questions.length * 100) + '%';

    const opts = document.getElementById('quizOptions');
    opts.innerHTML = '';
    q.opts.forEach(opt => {
      const btn = document.createElement('button');
      btn.className = 'quiz-opt';
      btn.textContent = opt;
      btn.onclick = nextQuestion;
      opts.appendChild(btn);
    });
    setTimeout(parseEmoji, 10);
  }

  function nextQuestion() {
    currentQ++;
    if (currentQ < questions.length) {
      renderQuestion();
    } else {
      document.getElementById('progressFill').style.width = '100%';
      setTimeout(() => showScreen('screen-final'), 400);
    }
  }

  // === Confetti ===
  function launchConfetti() {
    const burst = document.getElementById('confettiBurst');
    burst.innerHTML = '';
    const colors = ['#e91e63','#f48fb1','#ffd54f','#4fc3f7','#aed581','#ce93d8'];
    for (let i = 0; i < 60; i++) {
      const c = document.createElement('div');
      c.className = 'conf';
      c.style.left = Math.random() * 100 + 'vw';
      c.style.top = '-10px';
      c.style.background = colors[Math.floor(Math.random() * colors.length)];
      c.style.animationDelay = Math.random() * 0.8 + 's';
      c.style.animationDuration = (1.2 + Math.random() * 0.8) + 's';
      c.style.width = (6 + Math.random() * 8) + 'px';
      c.style.height = (6 + Math.random() * 8) + 'px';
      burst.appendChild(c);
    }
    setTimeout(() => burst.innerHTML = '', 3000);
  }

  // === Restart ===
  function restart() {
    const noBtn = document.getElementById('noBtn');
    noBtn.style.left = '0px';
    noBtn.style.top = '0px';
    showScreen('screen-main');
  }
</script>
</body>
</html>
