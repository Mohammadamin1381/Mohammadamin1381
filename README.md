<!--Hello, this is a code for making a simple calculator on the web using HTML-Css-JS. I hope you use it and enjoy it.-->
<!--سلام این یک کد ساخت یک ماشین حساب ساده در وب با استفاده از HTML-Css-JS هست امیدوارم استفاده کنید و لذت ببرید-->


<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title> calculator </title>
    <style>
      .calculator {
        margin: auto;
        width: 500px;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 15px;
      }
      .display {
        background-color:#f5f5f5;
        border: 2px solid #ccc;
        border-radius: 10px;
        padding: 10px;
        text-align: right;
        margin-bottom: 10px;
      }
      .buttons {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 7px;
      }
      button {
        background-color: #f5f5f5;
        border: 1px solid #ccc;
        border-radius: 10px;
        font-size: 20px;
        padding: 10px;
        cursor: pointer;
      }
      .number {
        grid-column: span 1;
      }
      .operator {
        grid-column: span 1;
      }
      .clear {
        grid-column: span 2;
      }
      .equal {
        grid-column: span 2;
      }
      center {
        color: red;
      }
    </style>
  </head>
  <body>
    <div class="calculator">
      <div class="display">
        <input type="text" id="input" readonly>
      </div>
      <div class="buttons">
        <button class="number">1</button>
        <button class="number">2</button>
        <button class="number">3</button>
        <button class="operator">+</button>
        <button class="number">4</button>
        <button class="number">5</button>
        <button class="number">6</button>
        <button class="operator">-</button>
        <button class="number">7</button>
        <button class="number">8</button>
        <button class="number">9</button>
        <button class="operator">x</button>
        <button class="number">.</button>
        <button class="number">0</button>
        <button class="operator">%</button>
        <button class="clear">C</button>
        <button class="equal">=</button>
      </div>
    </div>
    <script>
      const input = document.getElementById('input');
      const buttons = document.querySelectorAll('.buttons button');
      let currentInput = '';
      let previousInput = '';
      let operation = '';
      function updateInput(value) {
        currentInput += value;
        input.value = currentInput;
      }
      function clearInput() {
        currentInput = '';
        previousInput = '';
        operation = '';
        input.value = '';
      }
      function calculate() {
        let result = 0;
        switch (operation) {
          case '+':
            result = parseFloat(previousInput) + parseFloat(currentInput);
            break;
          case '-':
            result = parseFloat(previousInput) - parseFloat(currentInput);
            break;
          case '*':
            result = parseFloat(previousInput) * parseFloat(currentInput);
            break;
          case '/':
            result = parseFloat(previousInput) / parseFloat(currentInput);
            break;
          default:
            result = parseFloat(currentInput);
        }
        input.value = result;
        currentInput = result.toString();
        previousInput = '';
        operation = '';
      }
      buttons.forEach(button => {
        button.addEventListener('click', () => {
          const value = button.textContent;
          if (!isNaN(value)) {
            updateInput(value);
          } else if (value === '.') {
            if (currentInput.indexOf('.') === -1) {
              updateInput(value);
            }
          } else if (value === 'C') {
            clearInput();
          } else if (value === '=') {
            calculate();
          } else {
            operation = value;
            previousInput = currentInput;
            currentInput = '';
          }
        });
      });
    </script>
    <center> * created by -Mohammadamin- * </center>
  </body>
</html>
