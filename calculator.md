<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Basic Calculator</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f3f3f3;
      font-family: Arial, sans-serif;
    }

    .calculator {
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
      width: 260px;
    }

    .display {
      width: 100%;
      height: 50px;
      margin-bottom: 15px;
      padding: 10px;
      font-size: 1.5rem;
      text-align: right;
      border: none;
      background: #eee;
      border-radius: 8px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    button {
      padding: 20px;
      font-size: 1.2rem;
      border: none;
      border-radius: 8px;
      background: #007bff;
      color: white;
      cursor: pointer;
      transition: background 0.3s;
    }

    button:hover {
      background: #0056b3;
    }

    .operator {
      background: #28a745;
    }

    .operator:hover {
      background: #1e7e34;
    }

    .equal {
      grid-column: span 2;
      background: #ffc107;
      color: #000;
    }

    .equal:hover {
      background: #e0a800;
    }

    .clear {
      background: #dc3545;
    }

    .clear:hover {
      background: #a71d2a;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" class="display" disabled>
    <div class="buttons">
      <button class="clear">C</button>
      <button>/</button>
      <button>*</button>
      <button>-</button>

      <button>7</button>
      <button>8</button>
      <button>9</button>
      <button class="operator">+</button>

      <button>4</button>
      <button>5</button>
      <button>6</button>
      <button>.</button>

      <button>1</button>
      <button>2</button>
      <button>3</button>
      <button class="equal">=</button>

      <button>0</button>
    </div>
  </div>

  <script>
    const display = document.getElementById("display");
    const buttons = document.querySelectorAll("button");

    let currentInput = "";

    buttons.forEach(button => {
      button.addEventListener("click", () => {
        const value = button.textContent;

        if (value === "C") {
          currentInput = "";
          display.value = "";
        } else if (value === "=") {
          try {
            currentInput = eval(currentInput).toString(); // use eval for simplicity
            display.value = currentInput;
          } catch {
            display.value = "Error";
            currentInput = "";
          }
        } else {
          currentInput += value;
          display.value = currentInput;
        }
      });
    });
  </script>
</body>
</html>
