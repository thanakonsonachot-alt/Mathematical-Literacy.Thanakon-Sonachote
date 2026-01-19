<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ป.5</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
      font-family: 'Kanit', sans-serif;
    }
    
    @keyframes bounce-in {
      0% { transform: scale(0.8); opacity: 0; }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); opacity: 1; }
    }
    
    @keyframes coin-spin {
      0% { transform: rotateY(0deg); }
      100% { transform: rotateY(360deg); }
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    
    @keyframes sparkle {
      0%, 100% { opacity: 0; transform: scale(0); }
      50% { opacity: 1; transform: scale(1); }
    }
    
    @keyframes slide-up {
      from { transform: translateY(20px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }
    
    .bounce-in { animation: bounce-in 0.5s ease-out; }
    .coin-spin { animation: coin-spin 1s ease-in-out; }
    .float { animation: float 3s ease-in-out infinite; }
    .sparkle { animation: sparkle 0.6s ease-out; }
    .slide-up { animation: slide-up 0.4s ease-out; }
    
    .money-card {
      transition: all 0.3s ease;
    }
    
    .money-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    }
    
    .btn-primary {
      transition: all 0.2s ease;
    }
    
    .btn-primary:hover {
      transform: scale(1.02);
    }
    
    .btn-primary:active {
      transform: scale(0.98);
    }
    
    .progress-bar {
      transition: width 0.5s ease;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full">
  <div id="app-wrapper" class="h-full w-full overflow-auto" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);"><!-- หน้าหลัก -->
   <div id="home-screen" class="min-h-full p-4 md:p-6">
    <div class="max-w-4xl mx-auto"><!-- Header -->
     <header class="text-center mb-8 slide-up">
      <div class="inline-block p-4 bg-white/20 rounded-full mb-4 float">
       <svg class="w-16 h-16 text-yellow-300" viewbox="0 0 24 24" fill="currentColor"><circle cx="12" cy="12" r="10" fill="currentColor" /> <text x="12" y="16" text-anchor="middle" fill="#764ba2" font-size="10" font-weight="bold">
         ฿
        </text>
       </svg>
      </div>
      <h1 id="main-title" class="text-3xl md:text-4xl font-bold text-white mb-2">คณิตศาสตร์การเงิน ป.5</h1>
      <p id="welcome-text" class="text-white/90 text-lg">เรียนรู้เรื่องเงินอย่างสนุกสนาน! 🎉</p>
     </header><!-- Score Display -->
     <div class="bg-white/20 backdrop-blur rounded-2xl p-4 mb-6 slide-up" style="animation-delay: 0.1s;">
      <div class="flex justify-between items-center text-white">
       <div class="flex items-center gap-2"><span class="text-2xl">⭐</span> <span class="font-medium">คะแนนรวม:</span> <span id="total-score" class="text-2xl font-bold text-yellow-300">0</span>
       </div>
       <div class="flex items-center gap-2"><span class="text-2xl">🏆</span> <span id="level-display" class="font-medium">ระดับ: เริ่มต้น</span>
       </div>
      </div>
     </div><!-- Menu Cards -->
     <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6"><!-- การนับเงิน --> <button onclick="startGame('counting')" class="money-card bg-white rounded-2xl p-6 text-left slide-up" style="animation-delay: 0.2s;">
       <div class="flex items-center gap-4">
        <div class="w-16 h-16 bg-gradient-to-br from-green-400 to-emerald-500 rounded-xl flex items-center justify-center text-3xl">
         💰
        </div>
        <div>
         <h3 class="text-xl font-bold text-gray-800">การนับเงิน</h3>
         <p class="text-gray-500">ฝึกนับธนบัตรและเหรียญ</p>
        </div>
       </div></button> <!-- การทอนเงิน --> <button onclick="startGame('change')" class="money-card bg-white rounded-2xl p-6 text-left slide-up" style="animation-delay: 0.3s;">
       <div class="flex items-center gap-4">
        <div class="w-16 h-16 bg-gradient-to-br from-blue-400 to-indigo-500 rounded-xl flex items-center justify-center text-3xl">
         🛒
        </div>
        <div>
         <h3 class="text-xl font-bold text-gray-800">การทอนเงิน</h3>
         <p class="text-gray-500">คำนวณเงินทอนจากการซื้อของ</p>
        </div>
       </div></button> <!-- การออมเงิน --> <button onclick="startGame('saving')" class="money-card bg-white rounded-2xl p-6 text-left slide-up" style="animation-delay: 0.4s;">
       <div class="flex items-center gap-4">
        <div class="w-16 h-16 bg-gradient-to-br from-pink-400 to-rose-500 rounded-xl flex items-center justify-center text-3xl">
         🏦
        </div>
        <div>
         <h3 class="text-xl font-bold text-gray-800">การออมเงิน</h3>
         <p class="text-gray-500">วางแผนการออมเงิน</p>
        </div>
       </div></button> <!-- การซื้อขาย --> <button onclick="startGame('shopping')" class="money-card bg-white rounded-2xl p-6 text-left slide-up" style="animation-delay: 0.5s;">
       <div class="flex items-center gap-4">
        <div class="w-16 h-16 bg-gradient-to-br from-orange-400 to-amber-500 rounded-xl flex items-center justify-center text-3xl">
         🏪
        </div>
        <div>
         <h3 class="text-xl font-bold text-gray-800">การซื้อขาย</h3>
         <p class="text-gray-500">คำนวณราคาสินค้า</p>
        </div>
       </div></button>
     </div><!-- Tips Section -->
     <div class="bg-white/10 backdrop-blur rounded-2xl p-4 text-white slide-up" style="animation-delay: 0.6s;">
      <h4 class="font-bold mb-2 flex items-center gap-2"><span>💡</span> เคล็ดลับการเงิน</h4>
      <p id="tip-text" class="text-white/90">การออมเงินทุกวัน แม้เพียงเล็กน้อย จะรวมเป็นเงินก้อนใหญ่ได้!</p>
     </div><!-- Creator Info -->
     <div class="bg-white/10 backdrop-blur rounded-2xl p-4 text-white text-center slide-up mt-4" style="animation-delay: 0.7s;">
      <div class="flex items-center justify-center gap-2 mb-2"><span class="text-2xl">👨‍🎓</span>
       <h4 class="font-bold">ผู้สร้างเกม</h4>
      </div>
      <p id="creator-name" class="text-white/90 font-medium">เด็กชายธนกร โสนะโชติ ชั้นประถมศึกษาปีที่ 5/5</p>
      <p id="creator-program" class="text-white/80 text-sm">สาย MEP (Mini English Program)</p>
      <div class="flex justify-center gap-2 mt-2 text-lg"><span>🎯</span> <span>📚</span> <span>💻</span>
      </div>
     </div>
    </div>
   </div><!-- ห���้าเกม -->
   <div id="game-screen" class="min-h-full p-4 md:p-6 hidden">
    <div class="max-w-2xl mx-auto"><!-- Game Header -->
     <div class="flex justify-between items-center mb-6"><button onclick="goHome()" class="flex items-center gap-2 text-white hover:text-yellow-300 transition-colors">
       <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
       </svg><span>กลับหน้าหลัก</span> </button>
      <div class="flex items-center gap-4 text-white"><span>ข้อ <span id="current-question">1</span>/10</span> <span>⭐ <span id="game-score">0</span></span>
      </div>
     </div><!-- Progress Bar -->
     <div class="bg-white/20 rounded-full h-3 mb-6">
      <div id="progress-bar" class="progress-bar bg-yellow-400 h-3 rounded-full" style="width: 10%"></div>
     </div><!-- Question Card -->
     <div id="question-card" class="bg-white rounded-2xl p-6 mb-6 bounce-in">
      <div id="question-icon" class="text-center text-6xl mb-4">
       💰
      </div>
      <h2 id="question-title" class="text-xl font-bold text-gray-800 text-center mb-2">การนับเงิน</h2>
      <p id="question-text" class="text-gray-600 text-center text-lg mb-6">คำถามจะแสดงที่นี่</p><!-- Visual Money Display -->
      <div id="money-visual" class="flex flex-wrap justify-center gap-2 mb-6"></div><!-- Answer Input -->
      <div id="answer-section" class="space-y-4">
       <div class="flex items-center justify-center gap-2"><input type="number" id="answer-input" class="w-40 px-4 py-3 text-2xl font-bold text-center border-2 border-gray-300 rounded-xl focus:border-purple-500 focus:outline-none" placeholder="?"> <span class="text-2xl font-bold text-gray-600">บาท</span>
       </div><button onclick="checkAnswer()" class="btn-primary w-full py-4 bg-gradient-to-r from-purple-500 to-indigo-500 text-white text-xl font-bold rounded-xl shadow-lg"> ตรวจคำตอบ ✓ </button>
      </div><!-- Multiple Choice (for some questions) -->
      <div id="choices-section" class="hidden grid grid-cols-2 gap-3">
      </div>
     </div><!-- Feedback -->
     <div id="feedback" class="hidden text-center">
      <div id="feedback-content" class="bg-white rounded-2xl p-6 bounce-in">
       <div id="feedback-icon" class="text-6xl mb-4">
        🎉
       </div>
       <p id="feedback-text" class="text-xl font-bold text-gray-800 mb-2">ถูกต้อง!</p>
       <p id="feedback-explanation" class="text-gray-600 mb-4"></p><button onclick="nextQuestion()" class="btn-primary px-8 py-3 bg-gradient-to-r from-green-500 to-emerald-500 text-white font-bold rounded-xl"> ข้อถัดไป → </button>
      </div>
     </div>
    </div>
   </div><!-- หน้าสรุปผล -->
   <div id="result-screen" class="min-h-full p-4 md:p-6 hidden">
    <div class="max-w-md mx-auto text-center">
     <div class="bg-white rounded-3xl p-8 bounce-in">
      <div id="result-icon" class="text-8xl mb-4">
       🏆
      </div>
      <h2 class="text-3xl font-bold text-gray-800 mb-2">ยอดเยี่ยม!</h2>
      <p class="text-gray-600 mb-6">คุณทำได้ดีมาก</p>
      <div class="bg-gradient-to-r from-purple-100 to-indigo-100 rounded-2xl p-6 mb-6">
       <div class="text-5xl font-bold text-purple-600 mb-2"><span id="final-score">0</span>/10
       </div>
       <p class="text-gray-600">คะแนนที่ได้</p>
      </div>
      <div id="result-stars" class="flex justify-center gap-2 mb-6 text-4xl">
       ⭐⭐⭐
      </div>
      <p id="result-message" class="text-gray-600 mb-6">คุณเข้าใจเรื่องการเงินได้ดี!</p>
      <div class="space-y-3"><button onclick="startGame(currentGameType)" class="btn-primary w-full py-3 bg-gradient-to-r from-purple-500 to-indigo-500 text-white font-bold rounded-xl"> เล่นอีกครั้ง �� </button> <button onclick="goHome()" class="w-full py-3 bg-gray-100 text-gray-700 font-bold rounded-xl hover:bg-gray-200 transition-colors"> กลับหน้าหลัก 🏠 </button>
      </div>
     </div>
    </div>
   </div>
  </div>
  <script>
    // Default configuration
    const defaultConfig = {
      app_title: 'คณิตศาสตร์การเงิน ป.5',
      welcome_message: 'เรียนรู้เรื่องเงินอย่างสนุกสนาน!',
      creator_name: 'เด็กชายธนกร โสนะโชติ ชั้นประถมศึกษาปีที่ 5/5',
      creator_program: 'สาย MEP (Mini English Program)',
      background_color: '#667eea',
      card_color: '#ffffff',
      text_color: '#1f2937',
      primary_action_color: '#8b5cf6',
      secondary_action_color: '#6366f1'
    };
    
    let config = { ...defaultConfig };
    
    // Game state
    let currentGameType = '';
    let currentQuestion = 0;
    let gameScore = 0;
    let totalScore = 0;
    let questions = [];
    let correctAnswer = 0;
    
    // Tips for finance
    const tips = [
      'การออมเงินทุกวัน แม้เพียงเล็กน้อย จะรวมเป็นเงินก้อนใหญ่ได้!',
      'ก่อนซื้อของ ให้ถามตัวเองว่า "จำเป็นหรือแค่อยากได้?"',
      'การทำบัญชีรายรับรายจ่ายช่วยให้รู้ว่าเงินหายไปไหน',
      'ตั้งเป้าหมายการออมจะช่วยให้มีแรงจูงใจมากขึ้น',
      'เก็บเหรียญเล็กๆ รวมกันนานๆ จะกลายเป็นเงินมาก!'
    ];
    
    // Money denominations
    const banknotes = [1000, 500, 100, 50, 20];
    const coins = [10, 5, 2, 1];
    
    // Products for shopping game
    const products = [
      { name: 'ดินสอ', emoji: '✏️', price: 5 },
      { name: 'ยางลบ', emoji: '🩹', price: 8 },
      { name: 'ไม้บรรทัด', emoji: '📏', price: 15 },
      { name: 'สมุด', emoji: '📓', price: 25 },
      { name: 'ปากกา', emoji: '🖊️', price: 12 },
      { name: 'กล่องดินสอ', emoji: '📦', price: 45 },
      { name: 'น้ำดื่ม', emoji: '💧', price: 7 },
      { name: 'ขนมปัง', emoji: '🍞', price: 20 },
      { name: 'นม', emoji: '🥛', price: 15 },
      { name: 'ผลไม้', emoji: '🍎', price: 30 }
    ];
    
    // Generate money visual (banknotes and coins)
    function generateMoneyVisual(amount) {
      let visual = '';
      let remaining = amount;
      
      // Banknotes
      for (const note of banknotes) {
        while (remaining >= note) {
          const colors = {
            1000: 'from-gray-600 to-gray-700',
            500: 'from-purple-500 to-purple-600',
            100: 'from-red-500 to-red-600',
            50: 'from-blue-500 to-blue-600',
            20: 'from-green-500 to-green-600'
          };
          visual += `<div class="bg-gradient-to-br ${colors[note]} text-white px-3 py-2 rounded-lg font-bold text-sm shadow-md">${note}฿</div>`;
          remaining -= note;
        }
      }
      
      // Coins
      for (const coin of coins) {
        while (remaining >= coin) {
          const sizes = {
            10: 'w-10 h-10',
            5: 'w-9 h-9',
            2: 'w-8 h-8',
            1: 'w-7 h-7'
          };
          visual += `<div class="${sizes[coin]} bg-gradient-to-br from-yellow-400 to-yellow-500 rounded-full flex items-center justify-center font-bold text-xs shadow-md border-2 border-yellow-600">${coin}</div>`;
          remaining -= coin;
        }
      }
      
      return visual;
    }
    
    // Generate questions based on game type
    function generateQuestions(type) {
      const qs = [];
      
      for (let i = 0; i < 10; i++) {
        switch (type) {
          case 'counting':
            qs.push(generateCountingQuestion());
            break;
          case 'change':
            qs.push(generateChangeQuestion());
            break;
          case 'saving':
            qs.push(generateSavingQuestion());
            break;
          case 'shopping':
            qs.push(generateShoppingQuestion());
            break;
        }
      }
      
      return qs;
    }
    
    function generateCountingQuestion() {
      const amount = Math.floor(Math.random() * 500) + 10;
      return {
        icon: '💰',
        title: 'การนับเงิน',
        text: 'รวมเงินทั้งหมดเท่าไร?',
        visual: generateMoneyVisual(amount),
        answer: amount,
        explanation: `เงินทั้งหมดรวมกันได้ ${amount} บาท`
      };
    }
    
    function generateChangeQuestion() {
      const product = products[Math.floor(Math.random() * products.length)];
      const payOptions = [20, 50, 100, 500];
      const pay = payOptions.find(p => p > product.price) || 100;
      const change = pay - product.price;
      
      return {
        icon: '🛒',
        title: 'การทอนเงิน',
        text: `ซื้อ${product.name} ${product.emoji} ราคา ${product.price} บาท จ่ายเงิน ${pay} บาท จะได้เงินทอนเท่าไร?`,
        visual: '',
        answer: change,
        explanation: `${pay} - ${product.price} = ${change} บาท`
      };
    }
    
    function generateSavingQuestion() {
      const dailySave = [5, 10, 15, 20][Math.floor(Math.random() * 4)];
      const days = [7, 10, 14, 30][Math.floor(Math.random() * 4)];
      const total = dailySave * days;
      
      return {
        icon: '🏦',
        title: 'การออมเงิน',
        text: `ถ้าออมเงินวันละ ${dailySave} บาท เป็นเวลา ${days} วัน จะมีเงินเก็บเท่าไร?`,
        visual: '',
        answer: total,
        explanation: `${dailySave} × ${days} = ${total} บาท`
      };
    }
    
    function generateShoppingQuestion() {
      const numProducts = Math.floor(Math.random() * 2) + 2;
      const selectedProducts = [];
      const usedIndexes = new Set();
      
      while (selectedProducts.length < numProducts) {
        const idx = Math.floor(Math.random() * products.length);
        if (!usedIndexes.has(idx)) {
          usedIndexes.add(idx);
          selectedProducts.push(products[idx]);
        }
      }
      
      const total = selectedProducts.reduce((sum, p) => sum + p.price, 0);
      const productList = selectedProducts.map(p => `${p.emoji} ${p.name} ${p.price}฿`).join(', ');
      
      return {
        icon: '🏪',
        title: 'การซื้อขาย',
        text: `ซื้อของ: ${productList} ต้องจ่ายเงินทั้งหมดเท่าไร?`,
        visual: '',
        answer: total,
        explanation: `รวมราคาสินค้า = ${total} บาท`
      };
    }
    
    // Start game
    function startGame(type) {
      currentGameType = type;
      currentQuestion = 0;
      gameScore = 0;
      questions = generateQuestions(type);
      
      document.getElementById('home-screen').classList.add('hidden');
      document.getElementById('game-screen').classList.remove('hidden');
      document.getElementById('result-screen').classList.add('hidden');
      document.getElementById('feedback').classList.add('hidden');
      
      showQuestion();
    }
    
    // Show question
    function showQuestion() {
      const q = questions[currentQuestion];
      
      document.getElementById('question-card').classList.remove('hidden');
      document.getElementById('feedback').classList.add('hidden');
      
      document.getElementById('question-icon').textContent = q.icon;
      document.getElementById('question-title').textContent = q.title;
      document.getElementById('question-text').textContent = q.text;
      document.getElementById('money-visual').innerHTML = q.visual;
      document.getElementById('answer-input').value = '';
      document.getElementById('current-question').textContent = currentQuestion + 1;
      document.getElementById('game-score').textContent = gameScore;
      document.getElementById('progress-bar').style.width = `${((currentQuestion + 1) / 10) * 100}%`;
      
      correctAnswer = q.answer;
      
      // Animate card
      const card = document.getElementById('question-card');
      card.classList.remove('bounce-in');
      void card.offsetWidth;
      card.classList.add('bounce-in');
      
      // Focus input
      setTimeout(() => {
        document.getElementById('answer-input').focus();
      }, 300);
    }
    
    // Check answer
    function checkAnswer() {
      const userAnswer = parseInt(document.getElementById('answer-input').value);
      const q = questions[currentQuestion];
      const isCorrect = userAnswer === correctAnswer;
      
      document.getElementById('question-card').classList.add('hidden');
      document.getElementById('feedback').classList.remove('hidden');
      
      const feedbackContent = document.getElementById('feedback-content');
      feedbackContent.classList.remove('bounce-in');
      void feedbackContent.offsetWidth;
      feedbackContent.classList.add('bounce-in');
      
      if (isCorrect) {
        gameScore++;
        totalScore++;
        document.getElementById('feedback-icon').textContent = '🎉';
        document.getElementById('feedback-text').textContent = 'ถูกต้อง! เก่งมาก!';
        feedbackContent.style.borderColor = '#10b981';
        feedbackContent.style.borderWidth = '3px';
      } else {
        document.getElementById('feedback-icon').textContent = '😅';
        document.getElementById('feedback-text').textContent = `ไม่ถูกต้อง คำตอบคือ ${correctAnswer} บาท`;
        feedbackContent.style.borderColor = '#ef4444';
        feedbackContent.style.borderWidth = '3px';
      }
      
      document.getElementById('feedback-explanation').textContent = q.explanation;
      document.getElementById('game-score').textContent = gameScore;
      document.getElementById('total-score').textContent = totalScore;
      updateLevel();
    }
    
    // Next question
    function nextQuestion() {
      currentQuestion++;
      
      if (currentQuestion >= 10) {
        showResults();
      } else {
        showQuestion();
      }
    }
    
    // Show results
    function showResults() {
      document.getElementById('game-screen').classList.add('hidden');
      document.getElementById('result-screen').classList.remove('hidden');
      
      document.getElementById('final-score').textContent = gameScore;
      
      // Stars based on score
      let stars = '';
      let icon = '';
      let message = '';
      
      if (gameScore >= 9) {
        stars = '⭐⭐⭐';
        icon = '🏆';
        message = 'ยอดเยี่ยมมาก! คุณเป็นอัจฉริยะด้านการเงิน!';
      } else if (gameScore >= 7) {
        stars = '⭐⭐';
        icon = '🎖️';
        message = 'ดีมาก! คุณเข้าใจเรื่องการเงินได้ดี!';
      } else if (gameScore >= 5) {
        stars = '⭐';
        icon = '👍';
        message = 'พอใช้ได้! ลองฝึกเพิ่มอีกนะ!';
      } else {
        stars = '💪';
        icon = '📚';
        message = 'ต้องฝึกฝนเพิ่มเติม มาลองใหม่กันเถอะ!';
      }
      
      document.getElementById('result-stars').textContent = stars;
      document.getElementById('result-icon').textContent = icon;
      document.getElementById('result-message').textContent = message;
    }
    
    // Go home
    function goHome() {
      document.getElementById('home-screen').classList.remove('hidden');
      document.getElementById('game-screen').classList.add('hidden');
      document.getElementById('result-screen').classList.add('hidden');
      
      // Update tip
      const tipText = tips[Math.floor(Math.random() * tips.length)];
      document.getElementById('tip-text').textContent = tipText;
    }
    
    // Update level display
    function updateLevel() {
      let level = 'เริ่มต้น';
      if (totalScore >= 50) level = 'ผู้เชี่ยวชาญ 🌟';
      else if (totalScore >= 30) level = 'นักการเงินมือทอง 💰';
      else if (totalScore >= 20) level = 'นักออมเงิน 🏦';
      else if (totalScore >= 10) level = 'ผู้เรียนรู้ 📚';
      
      document.getElementById('level-display').textContent = `ระดับ: ${level}`;
    }
    
    // Handle enter key for answer input
    document.addEventListener('DOMContentLoaded', () => {
      document.getElementById('answer-input').addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
          checkAnswer();
        }
      });
    });
    
    // Apply config to UI
    function applyConfig(cfg) {
      document.getElementById('main-title').textContent = cfg.app_title || defaultConfig.app_title;
      document.getElementById('welcome-text').textContent = (cfg.welcome_message || defaultConfig.welcome_message) + ' 🎉';
      document.getElementById('creator-name').textContent = cfg.creator_name || defaultConfig.creator_name;
      document.getElementById('creator-program').textContent = cfg.creator_program || defaultConfig.creator_program;
      
      // Apply colors
      const bgColor = cfg.background_color || defaultConfig.background_color;
      document.getElementById('app-wrapper').style.background = `linear-gradient(135deg, ${bgColor} 0%, #764ba2 100%)`;
    }
    
    // Initialize Element SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange: async (newConfig) => {
          config = { ...defaultConfig, ...newConfig };
          applyConfig(config);
        },
        mapToCapabilities: (cfg) => ({
          recolorables: [
            {
              get: () => cfg.background_color || defaultConfig.background_color,
              set: (value) => {
                cfg.background_color = value;
                window.elementSdk.setConfig({ background_color: value });
              }
            },
            {
              get: () => cfg.card_color || defaultConfig.card_color,
              set: (value) => {
                cfg.card_color = value;
                window.elementSdk.setConfig({ card_color: value });
              }
            },
            {
              get: () => cfg.text_color || defaultConfig.text_color,
              set: (value) => {
                cfg.text_color = value;
                window.elementSdk.setConfig({ text_color: value });
              }
            },
            {
              get: () => cfg.primary_action_color || defaultConfig.primary_action_color,
              set: (value) => {
                cfg.primary_action_color = value;
                window.elementSdk.setConfig({ primary_action_color: value });
              }
            },
            {
              get: () => cfg.secondary_action_color || defaultConfig.secondary_action_color,
              set: (value) => {
                cfg.secondary_action_color = value;
                window.elementSdk.setConfig({ secondary_action_color: value });
              }
            }
          ],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (cfg) => new Map([
          ['app_title', cfg.app_title || defaultConfig.app_title],
          ['welcome_message', cfg.welcome_message || defaultConfig.welcome_message],
          ['creator_name', cfg.creator_name || defaultConfig.creator_name],
          ['creator_program', cfg.creator_program || defaultConfig.creator_program]
        ])
      });
    }
    
    // Initial setup
    applyConfig(config);
    updateLevel();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c032a63f6117323',t:'MTc2ODc5MjUwNS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
