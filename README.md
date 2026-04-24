# Fifa-tickets-booking-web-
A stylish and responsive front-end web project built using HTML, CSS, and JavaScript, designed for Real Madrid fans to explore upcoming matches, book tickets, and submit feedback. Features a yellow &amp; white theme inspired by Real Madrid, interactive booking forms, hover animations, and a smooth fan-focused UI.
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FIFA World Cup Tickets | Fan Portal</title>

<style>
:root {
    --primary: #0b3d91;
    --accent: #f5c518;
    --white: #ffffff;
    --dark: #111;
}

body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
}

/* HEADER */
header {
    background: var(--primary);
    color: white;
    padding: 15px;
    text-align: center;
}

/* HERO */
.hero {
    background: linear-gradient(135deg, var(--primary), #1e5ed6);
    color: white;
    height: 320px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

/* SECTION */
section {
    padding: 50px 20px;
    max-width: 1100px;
    margin: auto;
}

/* MATCH CARDS */
.matches {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
}

.match {
    border: 2px solid var(--accent);
    padding: 20px;
    border-radius: 10px;
    text-align: center;
    transition: 0.3s;
}

.match:hover {
    transform: scale(1.05);
}

/* FORM */
form {
    border: 2px solid var(--accent);
    padding: 25px;
    border-radius: 10px;
    background: #f9f9f9;
}

input, select, textarea, button {
    width: 100%;
    padding: 10px;
    margin-bottom: 12px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

button {
    background: var(--accent);
    border: none;
    font-weight: bold;
    cursor: pointer;
}

button:hover {
    background: #e0b000;
}

.success {
    color: green;
    text-align: center;
    font-weight: bold;
}

/* FOOTER */
footer {
    background: var(--dark);
    color: white;
    text-align: center;
    padding: 20px;
}
</style>
</head>

<body>

<header>
    <h1>🏆 FIFA WORLD CUP 2026</h1>
</header>

<div class="hero">
    <h2>⚽ Book Your Match Tickets</h2>
    <p>Global Football Experience 🌍</p>
</div>

<section>
<h2>Upcoming Matches</h2>

<div class="matches">
    <div class="match">
        <h3>Argentina vs Brazil</h3>
        <p>📅 12 June 2026</p>
        <p>🏟️ New York Stadium</p>
    </div>

    <div class="match">
        <h3>France vs Germany</h3>
        <p>📅 15 June 2026</p>
        <p>🏟️ Los Angeles Stadium</p>
    </div>

    <div class="match">
        <h3>Spain vs England</h3>
        <p>📅 18 June 2026</p>
        <p>🏟️ Dallas Stadium</p>
    </div>
</div>
</section>

<section>
<h2>🎫 Ticket Booking</h2>

<form id="bookingForm">
    <input type="text" id="name" placeholder="Full Name" required>

    <select id="match" required>
        <option value="">Select Match</option>
        <option>Argentina vs Brazil</option>
        <option>France vs Germany</option>
        <option>Spain vs England</option>
    </select>

    <select id="seat" required>
        <option value="">Seat Type</option>
        <option>VIP</option>
        <option>Premium</option>
        <option>Regular</option>
    </select>

    <input type="number" id="tickets" placeholder="Number of Tickets" min="1" max="6" required>

    <button type="submit">Book Now</button>
    <p id="bookingMsg" class="success"></p>
</form>
</section>

<section>
<h2>💬 Fan Feedback</h2>

<form id="feedbackForm">
    <input type="text" id="fname" placeholder="Your Name" required>
    <textarea id="feedback" rows="4" placeholder="Your Feedback..." required></textarea>
    <button type="submit">Submit Feedback</button>
    <p id="feedbackMsg" class="success"></p>
</form>
</section>

<footer>
    <p>© 2026 FIFA World Cup Fan Portal 🌍</p>
</footer>

<script>
// BOOKING
document.getElementById("bookingForm").addEventListener("submit", function(e){
    e.preventDefault();

    let name = document.getElementById("name").value;
    let match = document.getElementById("match").value;
    let seat = document.getElementById("seat").value;
    let tickets = document.getElementById("tickets").value;

    if(name && match && seat && tickets){
        document.getElementById("bookingMsg").innerText =
        "✅ Ticket booked successfully for " + name;
        this.reset();
    } else {
        alert("Fill all fields");
    }
});

// FEEDBACK
document.getElementById("feedbackForm").addEventListener("submit", function(e){
    e.preventDefault();

    let name = document.getElementById("fname").value;
    let feedback = document.getElementById("feedback").value;

    if(name && feedback){
        document.getElementById("feedbackMsg").innerText =
        "🙏 Thanks for your feedback, " + name;
        this.reset();
    } else {
        alert("Fill all fields");
    }
});
</script>

</body>
</html>