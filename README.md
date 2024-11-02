<!DOCTYPE html>
<html lang="he">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>אתר שאלות ותשובות</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            color: #333;
            background-color: #f9f9f9;
            margin: 0;
            padding: 0;
        }

        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            background-color: #6200ea;
            color: #fff;
        }

        .container {
            padding: 20px;
            max-width: 600px;
            margin: auto;
        }

        .question {
            margin-bottom: 20px;
        }

        textarea {
            width: 100%;
            height: 60px;
            margin-bottom: 10px;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            resize: none;
        }

        button {
            padding: 10px 15px;
            color: #fff;
            background-color: #6200ea;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
        }

        .questions-list {
            border-top: 1px solid #ccc;
            padding-top: 10px;
        }

        /* מצב כהה */
        body.dark-mode {
            color: #eee;
            background-color: #121212;
        }

        .dark-mode .header {
            background-color: #333;
        }

        .dark-mode button {
            background-color: #555;
        }

        .badge {
            background-color: #4caf50;
            color: white;
            padding: 3px 5px;
            border-radius: 5px;
            font-size: 12px;
            margin-left: 5px;
        }

        .question-item {
            margin-bottom: 10px;
        }

        @media (max-width: 600px) {
            .header {
                flex-direction: column;
                align-items: flex-start;
            }

            button {
                margin-top: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>אתר שאלות ותשובות</h1>
        <button id="toggle-dark-mode">מצב כהה</button>
    </div>

    <div class="container">
        <div class="question">
            <h2>שאל שאלה:</h2>
            <textarea placeholder="הקלד את שאלתך כאן..." id="question-input"></textarea>
            <button id="submit-question">פרסם שאלה</button>
        </div>

        <div class="questions-list" id="questions-list">
            <h2>שאלות אחרונות</h2>
            <!-- שאלות יופיעו כאן -->
        </div>
    </div>

    <script>
        // פונקציה למעבר בין מצב כהה ואור
        const toggleDarkModeBtn = document.getElementById('toggle-dark-mode');
        toggleDarkModeBtn.addEventListener('click', () => {
            document.body.classList.toggle('dark-mode');
        });

        // פונקציה לפרסום שאלות
        document.getElementById('submit-question').addEventListener('click', function() {
            const textArea = document.getElementById('question-input');
            const questionText = textArea.value.trim();
            
            if (questionText === '') {
                alert("אנא הקלד שאלה לפני הפרסום."); // התראה אם השאלה ריקה
                return; // אם השאלה ריקה, לא עושים כלום
            }

            const questionDiv = document.createElement('div');
            questionDiv.classList.add('question-item');
            questionDiv.innerHTML = <p>${questionText}</p><span class="badge">נאמן</span>;
            
            document.getElementById('questions-list').appendChild(questionDiv);
            textArea.value = ''; // מנקה את השאלה לאחר פרסום
        });
    </script>
</body>
</html>
