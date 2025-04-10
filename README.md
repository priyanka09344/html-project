<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Enhanced Calculator</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(120deg, #4facfe, #00f2fe);
        }
        .calculator {
            width: 350px;
            background: #fff;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0px 8px 20px rgba(0, 0, 0, 0.2);
        }
        .display {
            margin-bottom: 20px;
            padding: 15px;
            background: #f3f3f3;
            text-align: right;
            font-size: 2em;
            border-radius: 10px;
            box-shadow: inset 0px 2px 5px rgba(0, 0, 0, 0.1);
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
        }
        button {
            padding: 20px;
            font-size: 1.2em;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            background: #4facfe;
            color: white;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
        }
        button:hover {
            background: #00c6ff;
        }
        button:active {
            background: #007acc;
        }
        button.special {
            background: #f95f62;
        }
        button.special:hover {
            background: #e04548;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button>7</button> <button>8</button> <button>9</button> <button>/</button>
            <button>4</button> <button>5</button> <button>6</button> <button>*</button>
            <button>1</button> <button>2</button> <button>3</button> <button>-</button>
            <button>0</button> <button>.</button> <button>=</button> <button>+</button>
            <button class="special">C</button> <button>√</button> <button>^</button> <button>%</button>
        </div>
    </div>
    <script>
        let display = document.getElementById("display");
        let buttons = Array.from(document.querySelectorAll("button"));
        let currentInput = "";

        buttons.forEach(button => {
            button.addEventListener("click", () => {
                const value = button.innerText;

                if (value === "=") {
                    try {
                        display.innerText = eval(currentInput);
                    } catch {
                        display.innerText = "Error";
                    }
                } else if (value === "C") {
                    currentInput = "";
                    display.innerText = "0";
                } else if (value === "√") {
                    currentInput = Math.sqrt(eval(currentInput)).toString();
                    display.innerText = currentInput;
                } else if (value === "^") {
                    currentInput += "";
                    display.innerText = currentInput;
                } else if (value === "%") {
                    currentInput = (eval(currentInput) / 100).toString();
                    display.innerText = currentInput;
                } else {
                    currentInput += value;
                    display.innerText = currentInput;
                }
            });
        });
    </script>
</body>
</html>
