<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Registration</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            background-color: #f9f9f9;
        }
        h1 {
            color: #333;
        }
        label {
            display: block;
            margin: 10px 0 5px;
        }
        input, select {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            padding: 10px 15px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>
    <h1>Welcome to Student Registration</h1>
    <form id="registrationForm">
        <label for="fullName">Full Name:</label>
        <input type="text" id="fullName" name="fullName" required>

        <label for="course">Select Course:</label>
        <select id="course" name="course" required>
            <option value="">Select a course</option>
            <option value="1">Adult Health Nursing</option>
            <option value="2">Internal Medicine</option>
            <option value="3">Pharmacology</option>
        </select>

        <button type="submit">Register</button>
    </form>

    <script>
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent the default form submission

            const fullName = document.getElementById('fullName').value;
            const courseId = document.getElementById('course').value;

            // Send data to the server
            fetch('http://localhost:4000/register', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    username: fullName,
                    courseId: courseId,
                    password: 'defaultPassword' // Replace or handle password securely
                })
            })
            .then(response => response.json())
            .then(data => {
                alert(data.message); // Show success message
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });
    </script>
</body>
</html>
