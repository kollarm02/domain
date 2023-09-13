<!-- src/Game.svelte -->
<script>
    let szam1 = 0;
    let szam2 = 0;
    let operator = '+';
    let valasz = '';
    let jovalasz = 0;
    let pontok = 0;
  
    function generateQuestion() {
      szam1 = Math.floor(Math.random() * 10);
      szam2 = Math.floor(Math.random() * 10);
      operator = ['+', '-', '*', '/'][Math.floor(Math.random() * 4)];
  
      switch (operator) {
        case '+':
          jovalasz = szam1 + szam2;
          break;
        case '-':
          jovalasz = szam1 - szam2;
          break;
        case '*':
          jovalasz = szam1 * szam2;
          break;
        case '/':
          jovalasz = (szam1 / szam2).toFixed(2);
          break;
      }
  
      valasz = '';
    }
  
    function checkAnswer() {
      if (valasz === jovalasz.toString()) {
        pontok++;
        generateQuestion();
      } else {
        alert('Helytelen válasz. Próbáld újra!');
        pontok = 0;
        generateQuestion();
      }
    }
    generateQuestion();
  </script>
  
  <h1>Matematikai készségfejlesztő</h1>
  
  
  <div class="question">
    <p>{szam1} {operator} {szam2} = </p>
    <input type="text" bind:value={valasz} />
    <button href="button" on:click={checkAnswer}>Ellenőrzés</button>
  </div>
  
  <div class="score">
    <p>Eredmény: {pontok}</p>
  </div>
 
  <style>
    /* Stílusoldal */
    h1 {
      text-align: left;
      margin-bottom: 500px;
      position:absolute;
      background-color:cadetblue
    }
  
    .question {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-top: 20px;
      vertical-align: middle;
      margin-left: 60px;
    }
  
    p {
      font-size: 24px;
      margin-right: 12px;
    }
  
    input {
      font-size: 24px;
      width: 50px;
      text-align: center;
      object-position: left;
      margin-right: 10px;
    }
  
    .score {
      text-align: center;
      margin-top: 10px;
      font-size: 24px;
      margin-left: 20px;
      background-color: chartreuse;
    }
  </style>
  