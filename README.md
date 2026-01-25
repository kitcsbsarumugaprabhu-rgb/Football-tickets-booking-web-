# Football-tickets-booking-web-
A stylish and responsive front-end web project built using HTML, CSS, and JavaScript, designed for Real Madrid fans to explore upcoming matches, book tickets, and submit feedback. Features a yellow &amp; white theme inspired by Real Madrid, interactive booking forms, hover animations, and a smooth fan-focused UI.
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Real Madrid Tickets | Fan Portal</title>

<style>
:root {
    --yellow: #FFD700;
    --white: #ffffff;
    --dark: #111;
}

body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: var(--white);
    color: var(--dark);
}
header {
    background: var(--white);
    border-bottom: 4px solid var(--yellow);
    padding: 15px 40px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.header-content {
    display: flex;
    align-items: center;
    gap: 20px;
}

.logo {
    width: 55px;
    height: 55px;
}

header h1 {
    margin: 0;
    color: #000;
}
.hero {
    background: linear-gradient(135deg, var(--yellow), #fff3b0);
    height: 380px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
}

.hero h2 {
    font-size: 48px;
    margin-bottom: 10px;
}
section {
    padding: 60px 20px;
    max-width: 1100px;
    margin: auto;
}

h2 {
    text-align: center;
    margin-bottom: 40px;
}
.matches {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 25px;
}

.match {
    background: var(--white);
    border: 2px solid var(--yellow);
    padding: 25px;
    border-radius: 15px;
    text-align: center;
    transition: 0.3s;
}

.match:hover {
    transform: translateY(-8px);
    box-shadow: 0 15px 30px rgba(0,0,0,0.1);
}

form {
    background: #fffef5;
    padding: 30px;
    border-radius: 15px;
    border: 2px solid var(--yellow);
}

input, select, textarea, button {
    width: 100%;
    padding: 12px;
    margin-bottom: 15px;
    border-radius: 8px;
    border: 1px solid #ccc;
    font-size: 15px;
}

button {
    background: var(--yellow);
    border: none;
    font-weight: bold;
    cursor: pointer;
}

button:hover {
    background: #ffcc00;
}

footer {
    background: var(--dark);
    color: white;
    text-align: center;
    padding: 40px;
}
</style>
</head>

<body>
<header>
    <div class="header-content">
        <h1>REAL MADRID FC</h1>
        <img src="https://upload.wikimedia.org/wikipedia/en/5/56/Real_Madrid_CF.svg" class="logo" alt="Football Logo">
    </div>
</header>
<div class="hero">
    <h2> Book Your Match Tickets </h2>
    <img src="https://cdn-icons-png.flaticon.com/512/53/53283.png" class="logo" alt="Football Logo">
    <p>Yellow & White | Premium Fan Experience</p>
</div>
<section>
<h2>Upcoming Premier League Matches</h2>

<div class="matches">
    <div class="match">
        <h3>Real Madrid vs Manchester City</h3>
        <p>📅 10 March 2026</p>
        <p>🏟️ Santiago Bernabéu</p>
    </div>

    <div class="match">
        <h3>Real Madrid vs Arsenal</h3>
        <p>📅 18 March 2026</p>
        <p>🏟️ Santiago Bernabéu</p>
    </div>

    <div class="match">
        <h3>Real Madrid vs Chelsea</h3>
        <p>📅 28 March 2026</p>
        <p>🏟️ Santiago Bernabéu</p>
    </div>
</div>
</section>
<section>
<h2>🎫 Ticket Booking</h2>

<form onsubmit="bookTicket(event)">
    <input type="text" placeholder="Full Name" required>

    <select required>
        <option value="">Select Match</option>
        <option>Man City</option>
        <option>Arsenal</option>
        <option>Chelsea</option>
    </select>

    <select required>
        <option value="">Seat Type</option>
        <option>VIP</option>
        <option>Premium</option>
        <option>Regular</option>
    </select>

    <input type="number" placeholder="Number of Tickets" min="1" max="6" required>

    <button type="submit">Book Now</button>
</form>
</section>
<section>
<h2>💬 Fan Feedback</h2>

<form onsubmit="sendFeedback(event)">
    <input type="text" placeholder="Your Name" required>
    <textarea rows="4" placeholder="Your Feedback..." required></textarea>
    <button type="submit">Submit Feedback</button>
</form>
</section>
<footer>
    <p>© 2026 Real Madrid Fan Portal | Hala Madrid 🤍💛</p>
</footer>

<script>
function bookTicket(e) {
    e.preventDefault();
    alert(" Ticket booked successfully! Confirmation sent.");
}

function sendFeedback(e) {
    e.preventDefault();
    alert(" Thank you for your feedback!");
}
</script>

</body>
</html>
