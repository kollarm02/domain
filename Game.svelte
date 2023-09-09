<script>
    let firstNumber = 0;
    let secondNumber = 0;
    let operator = '+';
    let userAnswer = '';
    let correctAnswer = 0;
    let score = 0;
  
    function generateQuestion() {
      firstNumber = Math.floor(Math.random() * 10);
      secondNumber = Math.floor(Math.random() * 10);
      operator = ['+', '-', '*', '/'][Math.floor(Math.random() * 4)];
  
      switch (operator) {
        case '+':
          correctAnswer = firstNumber + secondNumber;
          break;
        case '-':
          correctAnswer = firstNumber - secondNumber;
          break;
        case '*':
          correctAnswer = firstNumber * secondNumber;
          break;
        case '/':
          correctAnswer = (firstNumber / secondNumber).toFixed(2);
          break;
      }
  
      userAnswer = '';
    }
  
    function checkAnswer() {
      if (userAnswer === correctAnswer.toString()) {
        score++;
        generateQuestion();
      } else {
        alert('Helytelen válasz. Próbáld újra!');
        score = 0;
        generateQuestion();
      }
    }
    generateQuestion();
  </script>
  
  <h1>Matematikai készségfejlesztő</h1>
  
  <div class="question">
    <p class="szam1">{firstNumber} {operator} {secondNumber} = </p>
  </div>
    <input class="box" type="text" bind:value={userAnswer} />
    <button class="button" on:click={checkAnswer}>Ellenőrzés</button>
  
  <div class="score">
    <p>Eredmény: {score}</p>
  </div>
  
  <style>
    h1 {
      text-transform: capitalize;
      text-align: center;
      margin-bottom: 400px;
      background-color: blanchedalmond;
    }
  
    .szam1 {
      background-color: blanchedalmond;
      text-align: justify;
      margin-left: 10px;
      font-size: 50px;
    
    }

    .box {
      margin-right: 80px;
      margin-top: 20px;
      
    }
    
    .button {
      font-size: 20px;
      margin-top: 20px;
    }
    p {
      font-size: 24px;
    }
  
    input {
      font-size: 34px;
      width: 50px;
      text-align: center;
    }
  
    .score {
      text-align: center;
      margin-top: 20px;
      font-size: 24px;
    }
  </style>
  