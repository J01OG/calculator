<!DOCTYPE html>
<html>
<head>
    <title>SGPA Calculator</title>
    <style>
        .container {
            max-width: 500px;
            margin: 0 auto;
            padding: 20px;
        }

        h1 {
            text-align: center;
        }

        input[type="number"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
        }

        button {
            display: block;
            width: 100%;
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }

        #result {
            margin-top: 20px;
            font-weight: bold;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>SGPA Calculator</h1>
        <form id="marksForm">
            <label for="subject1">DBMS (Credit: 4):</label>
            <input type="number" id="subject1" required>

            <label for="subject2">AFL (Credit: 4):</label>
            <input type="number" id="subject2" required>

            <label for="subject3">COA (Credit: 4):</label>
            <input type="number" id="subject3" required>

            <label for="subject4">WT (Credit: 3):</label>
            <input type="number" id="subject4" required>

            <label for="subject5">OS (Credit: 3):</label>
            <input type="number" id="subject5" required>

            <label for="subject6"></label>
            <label for="subject6"></label>
            <select id="subject6-credit">
                <option value="3">DE (Credit: 3): </option>
                <option value="4">PDC (Credit: 4)</option>
            </select>
            <input type="number" id="subject6" required>

            <label for="subject7">DBMS(L) (Credit: 1):</label>
            <input type="number" id="subject7" required>

            <label for="subject8">WT(L) (Credit: 1):</label>
            <input type="number" id="subject8" required>

            <label for="subject9">OS(L) (Credit: 1):</label>
            <input type="number" id="subject9" required>

            <label for="subject10">BC(L) (Credit: 1):</label>
            <input type="number" id="subject10" required>

            <button type="submit">Calculate SGPA</button>
        </form>
        <div id="result"></div>
    </div>

    <script>
        document.getElementById('marksForm').addEventListener('submit', function(e) {
            e.preventDefault(); // Prevent form submission

            // Get the marks entered by the user
            const marks = [];
            for (let i = 1; i <= 10; i++) {
                const subjectId = 'subject' + i;
                const subjectMarks = parseInt(document.getElementById(subjectId).value);
                marks.push(subjectMarks);
            }

            // Define credits for each subject
            const credits = [4, 4, 4, 3, 3, 0, 1, 1, 1, 1];

            // Get the selected credit for subject 6
            const subject6Credit = parseInt(document.getElementById('subject6-credit').value);
            credits[5] = subject6Credit;

            

               
            let grade =0;
            let weightedSum = 0;
            for (let i = 0; i < marks.length; i++) {

                if(marks[i]>=90)
                grade=10;
                else
                if(marks[i]>=80)
                grade=9;
                else
                if(marks[i]>=70)
                grade=8;
                else
                if(marks[i]>=60)
                grade=7;
                else
                if(marks[i]>=50)
                grade=6;
                else
                if(marks[i]>=40)
                grade=5;
                else
                grade=2;

                weightedSum += grade*credits[i];
            }

            // Calculate the total credits
            const totalCredits = credits.reduce((a, b) => a + b, 0);

            // Calculate SGPA
            const sgpa = weightedSum / totalCredits;

            // Display the result
            document.getElementById('result').textContent = "SGPA: " + sgpa.toFixed(2);
        });
    </script>
</body>
</html>
