<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator App</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" disabled>
    <div class="buttons">
      <button class="digit" onclick="handleDigitClick(7)">7</button>
      <button class="digit" onclick="handleDigitClick(8)">8</button>
      <button class="digit" onclick="handleDigitClick(9)">9</button>
      <button class="operation" onclick="handleOperationClick('/')">/</button>
      <button class="digit" onclick="handleDigitClick(4)">4</button>
      <button class="digit" onclick="handleDigitClick(5)">5</button>
      <button class="digit" onclick="handleDigitClick(6)">6</button>
      <button class="operation" onclick="handleOperationClick('*')">*</button>
      <button class="digit" onclick="handleDigitClick(1)">1</button>
      <button class="digit" onclick="handleDigitClick(2)">2</button>
      <button class="digit" onclick="handleDigitClick(3)">3</button>
      <button class="operation" onclick="handleOperationClick('-')">-</button>
      <button class="digit" onclick="handleDigitClick(0)">0</button>
      <button class="clear" onclick="handleClearClick()">C</button>
      <button class="equals" onclick="handleEqualsClick()">=</button>
      <button class="operation" onclick="handleOperationClick('+')">+</button>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>
.calculator {
  width: 300px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

#display {
  width: 100%;
  height: 40px;
  font-size: 24px;
  text-align: right;
  padding: 10px;
  border: none;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 10px;
  margin-top: 20px;
}

button {
  height: 40px;
  font-size: 18px;
  border: none;
  border-radius: 10px;
  background-color: #f0f0f0;
  cursor: pointer;
}

button:hover {
  background-color: #e0e0e0;
}

.operation {
  background-color: #ff9900;
  color: #fff;
}

.equals {
  background-color: #4CAF50;
  color: #fff;
}

.clear {
  background-color: #e74c3c;
  color: #fff;
}
let currentNumber = '';
let previousNumber = '';
let operation = '';

function handleDigitClick(digit) {
  currentNumber += digit.toString();
  updateDisplay();
}

function handleOperationClick(op) {
  previousNumber = currentNumber;
  currentNumber = '';
  operation = op;
}

function handleEqualsClick() {
  let result;
  switch (operation) {
    case '+':
      result = parseFloat(previousNumber) + parseFloat(currentNumber);
      break;
    case '-':
      result = parseFloat(previousNumber) - parseFloat(currentNumber);
      break;
    case '*':
      result = parseFloat(previousNumber) * parseFloat(currentNumber);
      break;
    case '/':
      result = parseFloat(previousNumber) / parseFloat(currentNumber);
      break;
    default:
      result = 0;
  }
  currentNumber = result.toString();
  updateDisplay();
}

function handleClearClick() {
  currentNumber = '';
  previousNumber = '';
  operation = '';
  updateDisplay();
}

function updateDisplay() {
  document.getElementById('display').value = currentNumber;
}
