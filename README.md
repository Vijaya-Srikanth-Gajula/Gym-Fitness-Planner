🏋️‍♂️ Gym Fitness Planner
Gym Fitness Planner is a simple and interactive web application designed to help users create personalized workout and diet plans based on their fitness goals. It provides tailored recommendations for exercises and dietary choices for both men and women, catering to different goals like bulking, cutting, or maintaining a fit body.

🚀 Features
Personalized workout plans based on gender and fitness goals.

Customized diet recommendations for both vegetarian and non-vegetarian users.

Interactive and user-friendly interface with responsive design.

Dynamic animations for a visually appealing experience.

Lightweight and easy to navigate.

🛠️ Technologies Used
HTML for structure

CSS for styling and animations

JavaScript for interactivity

📌 How to Use
Select your gender.

Choose your fitness goal (e.g., Bulk, Lean Bulk, Cut, Lean Cut, Fit Body).

Pick your diet preference (Vegetarian or Non-Vegetarian).

Click Generate Plan to get a tailored workout and diet plan.

🌿 Future Enhancements
Add progress tracking.

Provide exercise demos through video links.

Implement a calorie calculator.

💡 Contributions
Feel free to fork this repository, submit issues, or contribute to improving this project.

code goes here
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gym Fitness Planner</title>
<link rel="icon" href="file:///C:/Users/vijay/OneDrive/Pictures/Screenshots/weblogo.png" type="image/png">
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-image: url('file:///C:/Users/vijay/OneDrive/Pictures/Screenshots/gymbg.png');
      background-size: cover;
      background-position: center;
      color: #333;
    }
    header {
      background-color: rgba(46, 134, 193, 0.9);
      color: white;
      padding: 1rem 0;
      text-align: center;
      font-size: 1.5rem;
    }
    main {
      padding: 20px;
    }
    section {
      background-color: rgba(255, 255, 255, 0.9);
      border-radius: 8px;
      margin-bottom: 20px;
      padding: 20px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }
    button {
      background-color: #2e86c1;
      color: white;
      border: none;
      padding: 10px 20px;
      cursor: pointer;
      border-radius: 5px;
      font-size: 1rem;
    }
    button:hover {
      background-color: #21618c;
    }
    select, input {
      padding: 10px;
      margin-top: 10px;
      margin-bottom: 20px;
      width: 100%;
      box-sizing: border-box;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 10px;
      text-align: center;
    }
    th {
      background-color: #2e86c1;
      color: white;
    }
    #workoutTable, #dietTable {
      background-color: rgba(46, 134, 193, 0.1);
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <header>Gym Fitness Planner</header>
  <main>
    <section>
      <h2>User Information</h2>
      <label for="gender">Select Gender:</label>
      <select id="gender">
        <option value="male">Male</option>
        <option value="female">Female</option>
      </select>

      <label for="goal">Select Body Goal:</label>
      <select id="goal">
        <option value="bulk">Bulk</option>
        <option value="lean-bulk">Lean Bulk</option>
        <option value="cut">Cut</option>
        <option value="lean-cut">Lean Cut</option>
        <option value="fit">Fit Body</option>
      </select>

      <label for="diet">Select Diet Type:</label>
      <select id="diet">
        <option value="veg">Vegetarian</option>
        <option value="non-veg">Non-Vegetarian</option>
      </select>

      <button onclick="generatePlan()">Generate Plan</button>
    </section>

    <section id="workoutPlan">
      <h2>Your Workout Plan</h2>
      <table id="workoutTable">
        <thead>
          <tr>
            <th>Exercise</th>
          </tr>
        </thead>
        <tbody></tbody>
      </table>
    </section>

    <section id="dietPlan">
      <h2>Your Diet Plan</h2>
      <table id="dietTable">
        <thead>
          <tr>
            <th>Diet Plan</th>
          </tr>
        </thead>
        <tbody></tbody>
      </table>
    </section>
  </main>

  <script>
    const workouts = {
      male: {
        bulk: ["Chest Press", "Deadlift", "Bench Press", "Squats", "Bicep Curls", "Overhead Press"],
        "lean-bulk": ["Push-ups", "Pull-ups", "Lunges", "Dumbbell Rows", "Tricep Dips", "Planks"],
        cut: ["Burpees", "Planks", "Mountain Climbers", "Jump Squats", "Jump Rope", "HIIT"],
        "lean-cut": ["Yoga", "Pilates", "HIIT", "Core Workouts", "Cycling", "Swimming"],
        fit: ["Running", "Cycling", "Bodyweight Exercises", "Swimming", "Hiking", "Yoga"]
      },
      female: {
        bulk: ["Deadlifts", "Hip Thrusts", "Squats", "Bench Press", "Romanian Deadlifts", "Leg Press"],
        "lean-bulk": ["Yoga", "Pilates", "Lunges", "Push-ups", "Kettlebell Swings", "Planks"],
        cut: ["Jumping Jacks", "Burpees", "Planks", "Sit-ups", "High Knees", "HIIT"],
        "lean-cut": ["Cardio", "Pilates", "HIIT", "Resistance Bands", "Boxing", "Rowing"],
        fit: ["Swimming", "Cycling", "Running", "Yoga", "Dancing", "Bodyweight Training"]
      }
    };

    const dietPlans = {
      bulk: { veg: ["Tofu", "Lentils", "Quinoa", "Nuts", "Avocados"], "non-veg": ["Chicken", "Eggs", "Salmon", "Rice", "Vegetables"] },
      "lean-bulk": { veg: ["Paneer", "Spinach", "Chickpeas", "Whole Grains", "Nuts"], "non-veg": ["Chicken Breast", "Fish", "Eggs", "Oats", "Vegetables"] },
      cut: { veg: ["Vegetable Salads", "Green Tea", "Sprouts", "Low-Carb Meals"], "non-veg": ["Grilled Chicken", "Eggs", "Fish", "Broccoli"] },
      "lean-cut": { veg: ["Quinoa", "Beans", "Leafy Greens", "Low-Fat Dairy"], "non-veg": ["Turkey Breast", "Cod Fish", "Eggs", "Leafy Greens"] },
      fit: { veg: ["Fruits", "Mixed Nuts", "Whole Grains", "Green Vegetables"], "non-veg": ["Egg Whites", "Chicken", "Fish", "Assorted Vegetables"] }
    };

    function generatePlan() {
      const gender = document.getElementById('gender').value;
      const goal = document.getElementById('goal').value;
      const dietType = document.getElementById('diet').value;
      const workoutTable = document.getElementById('workoutTable').querySelector('tbody');
      const dietTable = document.getElementById('dietTable').querySelector('tbody');

      workoutTable.innerHTML = workouts[gender][goal].map(exercise => `<tr><td>${exercise}</td></tr>`).join('');
      dietTable.innerHTML = dietPlans[goal][dietType].map(food => `<tr><td>${food}</td></tr>`).join('');
    }
  </script>
</body>
</html>
