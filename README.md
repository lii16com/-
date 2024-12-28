<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>إدارة المحفظة</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            direction: rtl;
            text-align: center;
            margin: 20px;
        }
        button {
            margin: 10px;
            padding: 10px 20px;
            font-size: 16px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <h1>إدارة المحفظة المالية</h1>
    <p id="income">💰 الراتب: 0 دينار</p>
    <p id="expenses">💸 المصروفات: 0 دينار</p>
    <button onclick="addIncome()">💰 إضافة راتب</button>
    <button onclick="addExpense()">💸 تسجيل مصروف</button>
    <button onclick="showHistory()">📊 عرض السجل</button>
    <script>
        let income = 0;
        let expenses = 0;
        const history = [];

        function addIncome() {
            const amount = parseFloat(prompt("أدخل مبلغ الراتب:"));
            if (!isNaN(amount) && amount > 0) {
                income += amount;
                history.push(`💰 إضافة راتب: ${amount} دينار`);
                updateUI();
            } else {
                alert("يرجى إدخال مبلغ صحيح.");
            }
        }

        function addExpense() {
            const amount = parseFloat(prompt("أدخل مبلغ المصروف:"));
            if (!isNaN(amount) && amount > 0) {
                expenses += amount;
                income -= amount;
                history.push(`💸 تسجيل مصروف: ${amount} دينار`);
                updateUI();
            } else {
                alert("يرجى إدخال مبلغ صحيح.");
            }
        }

        function showHistory() {
            if (history.length === 0) {
                alert("لا يوجد سجل حتى الآن.");
            } else {
                alert("📊 السجل:\n" + history.join("\n"));
            }
        }

        function updateUI() {
            document.getElementById("income").innerText = `💰 الراتب: ${income.toFixed(2)} دينار`;
            document.getElementById("expenses").innerText = `💸 المصروفات: ${expenses.toFixed(2)} دينار`;
        }
    </script>
</body>
</html>
