
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <script src="https://code.jquery.com/jquery-3.2.1.min.js" integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=" crossorigin="anonymous"></script>
    
    <style>
        /* Centering the body using Flexbox */
        body {
            background: linear-gradient(135deg, #6a11cb, #2575fc);
            background-size: 400% 400%;
            animation: gradientAnimation 15s ease infinite;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            color: #fff;
        }

        @keyframes gradientAnimation {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Calculator container centered and styled */
        .container {
            position: relative;
            z-index: 2;
            text-align: center;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(10px);
        }

        /* Display area */
        #resultArea {
            background-color: rgba(0, 0, 0, 0.6);
            color: #fff;
            font-size: 36px;
            text-align: right;
            padding: 15px;
            margin: 0 auto;
            border: none;
            border-radius: 15px;
            width: 80%;
            max-width: 400px;
            box-shadow: inset 0px 4px 8px rgba(0, 0, 0, 0.4);
        }

        /* Button styles */
        button {
            height: 60px;
            width: 60px;
            margin: 5px;
            font-size: 20px;
            border-radius: 50%;
            background-color: #e3e3e3;
            color: #000;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
            border: none;
            position: relative;
        }

        /* Invert button color on hover */
        button:hover {
            background-color: #000;
            color: #fff;
            transform: scale(1.1);
            box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.4);
        }

        /* Active button state */
        button:active {
            transform: scale(0.95);
            box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.5);
        }

        /* Special button styles (Clear and Equals) */
        #clrTxt, #eq {
            background-color: #ff7675;
            color: #fff;
        }

        #clrTxt:hover, #eq:hover {
            background-color: #fff;
            color: #ff7675;
            box-shadow: 0px 0px 30px rgba(255, 118, 117, 0.8);
            transform: scale(1.15);
        }

        /* Table layout to adjust the calculator buttons */
        table {
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="jumbotron">
            <h1 class="display-3" style="color: grey;">Simple Calculator </h1>
            <p class="lead" style="color: silver;">This Calculator was developed by <br><p style="color: aqua;">Chris Sikhosana</p>
            <hr class="my-4">
        </div>

        <textarea id="resultArea" readonly rows="1" cols="21"></textarea>
        
        <table>
            <!-- First Row (Clear, Delete, Parentheses) -->
            <tr>
                <td><button id="clrTxt" class="btn btn-danger">C</button></td>
                <td><button id="del" class="btn btn-default"><i class="material-icons" style="color:red">backspace</i></button></td>
                <td><button id="openParen" class="btn btn-default">(</button></td>
                <td><button id="closeParen" class="btn btn-default">)</button></td>
            </tr>
            <!-- Second Row (Numbers and Operators) -->
            <tr>
                <td><button id="num7" class="btn btn-default">7</button></td>
                <td><button id="num8" class="btn btn-default">8</button></td>
                <td><button id="num9" class="btn btn-default">9</button></td>
                <td><button id="opDiv" class="btn btn-default">&divide;</button></td>
            </tr>
            <tr>
                <td><button id="num4" class="btn btn-default">4</button></td>
                <td><button id="num5" class="btn btn-default">5</button></td>
                <td><button id="num6" class="btn btn-default">6</button></td>
                <td><button id="opMul" class="btn btn-default">&times;</button></td>
            </tr>
            <tr>
                <td><button id="num1" class="btn btn-default">1</button></td>
                <td><button id="num2" class="btn btn-default">2</button></td>
                <td><button id="num3" class="btn btn-default">3</button></td>
                <td><button id="opSub" class="btn btn-default">&minus;</button></td>
            </tr>
            <!-- Decimal, 0, Equals, Addition -->
            <tr>
                <td><button id="decp" class="btn btn-default">.</button></td>
                <td><button id="num0" class="btn btn-default">0</button></td>
                <td><button id="eq" class="btn btn-default">=</button></td>
                <td><button id="opAdd" class="btn btn-default">&plus;</button></td>
            </tr>
            <!-- Advanced Scientific Functions -->
            <tr>
                <td><button id="sqrt" class="btn btn-default">√</button></td>
                <td><button id="pow" class="btn btn-default">x²</button></td>
                <td><button id="log" class="btn btn-default">log</button></td>
                <td><button id="exp" class="btn btn-default">exp</button></td>
            </tr>
            <tr>
                <td><button id="sin" class="btn btn-default">sin</button></td>
                <td><button id="cos" class="btn btn-default">cos</button></td>
                <td><button id="tan" class="btn btn-default">tan</button></td>
                <td><button id="ln" class="btn btn-default">ln</button></td>
            </tr>
            <tr>
                <td><button id="mAdd" class="btn btn-default">M+</button></td>
                <td><button id="mSub" class="btn btn-default">M-</button></td>
                <td><button id="mRecall" class="btn btn-default">MR</button></td>
                <td><button id="mClear" class="btn btn-default">MC</button></td>
            </tr>
        </table>
    </div>

    <script type="text/javascript">
        let expression = "";
        let memory = 0;

        const resultArea = document.querySelector("#resultArea");

        // Helper functions
        function updateResult(value) {
            resultArea.value = value;
        }

        // Basic and Scientific Operation Logic
        function evaluateExpression() {
            try {
                return eval(expression.replace("×", "*").replace("÷", "/"));
            } catch {
                return "Error";
            }
        }

        document.querySelectorAll("button").forEach(button => {
            button.addEventListener("click", function() {
                const buttonContent = button.textContent;

                if (buttonContent === "=") {
                    expression = evaluateExpression();
                    updateResult(expression);
                } else if (buttonContent === "C") {
                    expression = "";
                    updateResult("");
                } else if (buttonContent === "backspace") {
                    expression = expression.slice(0, -1);
                    updateResult(expression);
                } else if (buttonContent === "√") {
                    expression = Math.sqrt(evaluateExpression());
                    updateResult(expression);
                } else if (buttonContent === "x²") {
                    expression = Math.pow(evaluateExpression(), 2);
                    updateResult(expression);
                } else if (buttonContent === "log") {
                    expression = Math.log10(evaluateExpression());
                    updateResult(expression);
                } else if (buttonContent === "exp") {
                    expression = Math.exp(evaluateExpression());
                    updateResult(expression);
                } else if (buttonContent === "sin") {
                    expression = Math.sin(evaluateExpression());
                    updateResult(expression);
                } else if (buttonContent === "cos") {
                    expression = Math.cos(evaluateExpression());
                    updateResult(expression);
                } else if (buttonContent === "tan") {
                    expression = Math.tan(evaluateExpression());
                    updateResult(expression);
                } else if (buttonContent === "ln") {
                    expression = Math.log(evaluateExpression());
                    updateResult(expression);
                } else if (buttonContent === "M+") {
                    memory += parseFloat(evaluateExpression());
                } else if (buttonContent === "M-") {
                    memory -= parseFloat(evaluateExpression());
                } else if (buttonContent === "MR") {
                    expression = memory;
                    updateResult(memory);
                } else if (buttonContent === "MC") {
                    memory = 0;
                } else {
                    expression += buttonContent;
                    updateResult(expression);
                }
            });
        });
    </script>
</body>
</html>
