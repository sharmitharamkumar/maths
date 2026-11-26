# Ex.No:06 JavaScript Calculator

## Date: 26/11/2026

## AIM

To design and develop a simple calculator using HTML, CSS, and JavaScript to perform basic arithmetic operations such as addition, subtraction, multiplication, and division.

## ALGORITHM

1. Create an HTML page to design the calculator interface.
2. Create a display field to show the numbers and calculation results.
3. Create buttons for digits from 0 to 9 and arithmetic operators.
4. Use CSS to arrange and style the calculator buttons and display.
5. Write JavaScript functions to handle button clicks.
6. Store the entered numbers and operators in the calculator display.
7. Use JavaScript to evaluate the arithmetic expression.
8. Display the calculated result on the calculator screen.
9. Provide a clear button to reset the calculator.
10. Test the calculator with different arithmetic operations.

## PROGRAM

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #e8eef7;
    }

    .calculator {
      width: 320px;
      padding: 20px;
      background: #1f2937;
      border-radius: 16px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
    }

    #display {
      width: 100%;
      height: 70px;
      margin-bottom: 20px;
      padding: 0 15px;
      font-size: 2rem;
      text-align: right;
      color: #ffffff;
      background: #111827;
      border: none;
      border-radius: 10px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    button {
      height: 60px;
      font-size: 1.3rem;
      color: #ffffff;
      background: #374151;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }

    button:hover {
      background: #4b5563;
    }

    button:active {
      transform: scale(0.95);
    }

    .op {
      background: #f59e0b;
    }

    .op:hover {
      background: #d98a06;
    }

    .clear {
      background: #ef4444;
    }

    .clear:hover {
      background: #dc2626;
    }

    .equal {
      background: #10b981;
      grid-row: span 2;
      height: auto;
    }

    .equal:hover {
      background: #059669;
    }

    .zero {
      grid-column: span 2;
    }
  </style>
</head>

<body>
  <div class="calculator">
    <input type="text" id="display" placeholder="0" readonly>

    <div class="buttons">
      <button class="clear" onclick="clearDisplay()">C</button>
      <button class="op" onclick="appendValue('/')">/</button>
      <button class="op" onclick="appendValue('*')">*</button>
      <button class="op" onclick="deleteLast()">DEL</button>

      <button onclick="appendValue('7')">7</button>
      <button onclick="appendValue('8')">8</button>
      <button onclick="appendValue('9')">9</button>
      <button class="op" onclick="appendValue('-')">-</button>

      <button onclick="appendValue('4')">4</button>
      <button onclick="appendValue('5')">5</button>
      <button onclick="appendValue('6')">6</button>
      <button class="op" onclick="appendValue('+')">+</button>

      <button onclick="appendValue('1')">1</button>
      <button onclick="appendValue('2')">2</button>
      <button onclick="appendValue('3')">3</button>
      <button class="equal" onclick="calculate()">=</button>

      <button class="zero" onclick="appendValue('0')">0</button>
      <button onclick="appendValue('.')">.</button>
    </div>
  </div>

  <script>
    const display = document.getElementById("display");

    // Add a number or operator to the display
    function appendValue(value) {
      display.value += value;
    }

    // Clear the whole display
    function clearDisplay() {
      display.value = "";
    }

    // Remove the last character
    function deleteLast() {
      display.value = display.value.slice(0, -1);
    }

    // Evaluate the expression and show the result
    function calculate() {
      const expression = display.value;

      if (expression === "") {
        return;
      }

      // Allow only digits, operators and decimal point
      if (!/^[0-9+\-*/. ]+$/.test(expression)) {
        display.value = "Error";
        return;
      }

      try {
        const result = Function("return " + expression)();

        if (!isFinite(result)) {
          display.value = "Cannot divide by 0";
        } else {
          display.value = result;
        }
      } catch (error) {
        display.value = "Error";
      }
    }
  </script>
</body>
</html>
```

## OUTPUT

![Output](calculator%20output.png.png)

## RESULT

Thus, a JavaScript-based calculator was successfully designed and developed to perform basic arithmetic operations using HTML, CSS, and JavaScript.
