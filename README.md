<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>School Calculator</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background-color: #f4f4f4; }
        #calculator, #fakeScreen { width: 300px; margin: 50px auto; padding: 20px; background: white; border-radius: 10px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2); }
        #screen { width: 100%; height: 50px; text-align: right; font-size: 20px; margin-bottom: 10px; }
        .buttons { display: grid; grid-template-columns: repeat(4, 1fr); gap: 5px; }
        button { padding: 15px; font-size: 18px; border: none; cursor: pointer; background: #ddd; border-radius: 5px; }
        button:hover { background: #ccc; }
        #teacherMode { width: 100%; margin-top: 10px; background: red; color: white; }
        #fakeScreen { display: none; }
        #fakeScreen h2 { color: blue; }
    </style>
</head>
<body>

    <div id="calculator">
        <input type="text" id="screen" readonly>
        <div class="buttons">
            <button onclick="clearScreen()">C</button>
            <button onclick="appendValue('7')">7</button>
            <button onclick="appendValue('8')">8</button>
            <button onclick="appendValue('9')">9</button>
            <button onclick="appendValue('/')">/</button>

            <button onclick="appendValue('4')">4</button>
            <button onclick="appendValue('5')">5</button>
            <button onclick="appendValue('6')">6</button>
            <button onclick="appendValue('*')">*</button>

            <button onclick="appendValue('1')">1</button>
            <button onclick="appendValue('2')">2</button>
            <button onclick="appendValue('3')">3</button>
            <button onclick="appendValue('-')">-</button>

            <button onclick="appendValue('0')">0</button>
            <button onclick="appendValue('.')">.</button>
            <button onclick="calculateResult()">=</button>
            <button onclick="appendValue('+')">+</button>
        </div>

        <button id="teacherMode" onclick="toggleTeacherMode()">👀 Teacher Mode</button>
    </div>

    <div id="fakeScreen">
        <h2>Math Notes</h2>
        <p>Finding the derivative of f(x)...</p>
        <p>Solving linear equations...</p>
        <p>Reviewing geometry formulas...</p>
    </div>

    <script>
        let isTeacherMode = false;

        function appendValue(value) {
            document.getElementById('screen').value += value;
        }

        function clearScreen() {
            document.getElementById('screen').value = '';
        }

        function calculateResult() {
            try {
                document.getElementById('screen').value = eval(document.getElementById('screen').value);
            } catch {
                document.getElementById('screen').value = "Error";
            }
        }

        function toggleTeacherMode() {
            isTeacherMode = !isTeacherMode;
            document.getElementById('calculator').style.display = isTeacherMode ? 'none' : 'block';
            document.getElementById('fakeScreen').style.display = isTeacherMode ? 'block' : 'none';
        }
    </script>

</body>
</html>
