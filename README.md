# Fifa-tickets-booking-web-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FIFA World Cup 2026 | Premium Tickets</title>

<style>
:root {
    --blue:#0a1f44;
    --blue2:#123d8c;
    --gold:#f5c518;
}

body {
    margin:0;
    font-family:Arial;
    background:linear-gradient(135deg,var(--blue),var(--blue2));
    color:white;
}

header {
    text-align:center;
    padding:15px;
    font-size:22px;
}

.matches {
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:20px;
    padding:20px;
}

.card {
    background:rgba(255,255,255,0.1);
    padding:15px;
    border-radius:10px;
    backdrop-filter:blur(10px);
}

.form-box {
    margin:20px;
    padding:20px;
    background:rgba(255,255,255,0.1);
    border-radius:10px;
}

input,select,button {
    width:100%;
    padding:10px;
    margin:8px 0;
    border:none;
    border-radius:6px;
}

button {
    background:var(--gold);
    font-weight:bold;
    cursor:pointer;
}

.seats {
    display:grid;
    grid-template-columns:repeat(6,1fr);
    gap:5px;
    margin-top:10px;
}

.seat {
    padding:10px;
    text-align:center;
    background:white;
    color:black;
    cursor:pointer;
    border-radius:5px;
}

.selected { background:green; color:white; }
.booked { background:red; color:white; cursor:not-allowed; }

.summary {
    margin-top:10px;
    background:rgba(0,0,0,0.3);
    padding:10px;
    border-radius:8px;
}

.ticket {
    background:rgba(255,255,255,0.1);
    padding:10px;
    margin:10px;
    border-left:5px solid gold;
}

.payment {
    display:none;
    padding:20px;
}
</style>
</head>

<body>

<header>🏆 FIFA WORLD CUP 2026</header>

<div class="matches" id="matches"></div>

<div class="form-box">
<h2>🎫 Book Ticket</h2>

<input type="text" id="name" placeholder="Your Name">

<select id="match"></select>

<select id="seatType">
<option value="">Seat Type</option>
<option value="VIP">VIP ($200)</option>
<option value="Premium">Premium ($120)</option>
<option value="Regular">Regular ($60)</option>
</select>

<h3>Select Seats</h3>
<div class="seats" id="seatGrid"></div>

<div class="summary" id="summary">Select seats to see price</div>

<button onclick="goPayment()">Proceed to Payment</button>
</div>

<div class="payment" id="paymentPage">
<h2>💳 Payment</h2>

<input type="text" placeholder="Card Number">
<input type="text" placeholder="Expiry Date">
<input type="text" placeholder="CVV">

<button onclick="confirmBooking()">Pay Now</button>
</div>

<h2 style="padding-left:20px;">📄 Your Tickets</h2>
<div id="tickets"></div>

<script>
const matches = [
 {t:"Argentina vs Brazil",d:"2026-06-12",v:"New York"},
 {t:"France vs Germany",d:"2026-06-15",v:"LA"},
 {t:"Spain vs England",d:"2026-06-18",v:"Dallas"}
];

let selectedSeats=[];

function loadMatches(){
 let html="",opt="<option value=''>Select Match</option>";
 matches.forEach(m=>{
  let days=Math.ceil((new Date(m.d)-new Date())/(1000*60*60*24));
  html+=`<div class='card'><h3>${m.t}</h3>
  <p>${m.d}</p><p>${m.v}</p><p>⏳ ${days} days left</p></div>`;
  opt+=`<option>${m.t}</option>`;
 });
 document.getElementById("matches").innerHTML=html;
 document.getElementById("match").innerHTML=opt;
}

function createSeats(){
 let grid="";
 for(let i=1;i<=30;i++){
  grid+=`<div class='seat' onclick="toggleSeat(this)">${i}</div>`;
 }
 document.getElementById("seatGrid").innerHTML=grid;
}

function toggleSeat(el){
 if(el.classList.contains("booked")) return;

 el.classList.toggle("selected");
 let num=el.innerText;

 if(selectedSeats.includes(num)){
  selectedSeats=selectedSeats.filter(s=>s!==num);
 } else {
  selectedSeats.push(num);
 }

 updateSummary();
}

function updateSummary(){
 let type=document.getElementById("seatType").value;
 let priceMap={VIP:200,Premium:120,Regular:60};

 if(type && selectedSeats.length){
  let total=priceMap[type]*selectedSeats.length;
  document.getElementById("summary").innerHTML=
  `Seats: ${selectedSeats.join(", ")}<br>💰 Total: $${total}`;
 }
}

document.getElementById("seatType").addEventListener("change",updateSummary);

function goPayment(){
 if(!selectedSeats.length){
  alert("Select seats");
  return;
 }
 document.querySelector(".form-box").style.display="none";
 document.getElementById("paymentPage").style.display="block";
}

function confirmBooking(){
 let name=document.getElementById("name").value;
 let match=document.getElementById("match").value;
 let type=document.getElementById("seatType").value;

 let ticket={
  id:"FIFA"+Math.floor(Math.random()*99999),
  name,match,type,seats:selectedSeats
 };

 let data=JSON.parse(localStorage.getItem("tickets"))||[];
 data.push(ticket);
 localStorage.setItem("tickets",JSON.stringify(data));

 alert("Payment Successful 🎉");
 displayTickets();
 location.reload();
}

function displayTickets(){
 let data=JSON.parse(localStorage.getItem("tickets"))||[];
 let html="";
 data.forEach(t=>{
  html+=`<div class='ticket'>
  🎫 ${t.id}<br>
  ${t.name} | ${t.match}<br>
  ${t.type} | Seats: ${t.seats.join(",")}
  </div>`;
 });
 document.getElementById("tickets").innerHTML=html;
}

loadMatches();
createSeats();
displayTickets();
</script>

</body>
</html>