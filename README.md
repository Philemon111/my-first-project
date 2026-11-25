

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Daily Challenge</title>
<style>
body {
  font-family: Arial, sans-serif;
  background: #101827;
  color: white;
  text-align: center;
  padding: 25px;
}
.card {
  background: #1e293b;
  padding: 25px;
  border-radius: 18px;
  margin-top: 30px;
}
button {
  background: #16a34a;
  color: white;
  border: none;
  padding: 15px 25px;
  border-radius: 10px;
  font-size: 16px;
  margin-top: 20px;
}
h1 { color: #38bdf8; }
</style>
</head>
<body>

<h1>Daily Challenge</h1>
<p>Welcome! Make today count.</p>

<div class="card">
  <h2>Today's Challenge</h2>
  <p>Complete 20 minutes of exercise today!</p>
  <h3 id="points">Points: 0</h3>
  <button id="complete">Complete Challenge</button>
  <p id="message"></p>
</div>

<script>
let points = Number(localStorage.getItem("points")) || 0;
let completed = localStorage.getItem("completed") ===
  new Date().toDateString();

document.getElementById("points").textContent =
  "Points: " + points;

const button = document.getElementById("complete");

if (completed) {
  button.disabled = true;
  button.textContent = "Completed Today!";
}

button.addEventListener("click", function() {
  if (completed) return;

  points += 10;
  localStorage.setItem("points", points);
  localStorage.setItem("completed", new Date().toDateString());

  document.getElementById("points").textContent =
    "Points: " + points;

  document.getElementById("message").textContent =
    "Congratulations! You earned 10 points!";

  button.disabled = true;
  button.textContent = "Completed Today!";
});
</script>

</body>
</html>
