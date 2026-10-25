
<!DOCTYPE html>
<html lang="sw">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WESTERN EAGLE TICKETING</title>
<style>
body{margin:0;font-family:Arial,sans-serif;background:#f2f5f9;color:#172033}
header{background:#102b55;color:white;text-align:center;padding:25px 15px}
main{max-width:650px;margin:25px auto;padding:0 15px}
.card{background:white;padding:24px;border-radius:12px;box-shadow:0 3px 15px #0001}
label{display:block;margin-top:15px;font-weight:bold}
input,select{box-sizing:border-box;width:100%;padding:12px;margin-top:7px;border:1px solid #ccd3df;border-radius:6px}
.total{margin-top:20px;padding:15px;background:#eef4ff;border-radius:8px;font-size:18px}
button{width:100%;padding:14px;margin-top:22px;background:#e4a629;border:0;border-radius:6px;font-weight:bold;font-size:16px;cursor:pointer}
footer{text-align:center;padding:25px;color:#566176}
</style>
</head>
<body>
<header>
<h1>WESTERN EAGLE</h1>
<p>ENTERTAINMENT MINISTRY</p>
<h2>MFUMO WA TIKETI</h2>
</header>
<main>
<section class="card">
<h2>Fomu ya Kuomba Tiketi</h2>
<form id="ticketForm">
<label for="name">Jina kamili la mteja</label>
<input id="name" type="text" required>

<label for="phone">Namba ya simu</label>
<input id="phone" type="tel" required>

<label for="event">Jina la tukio</label>
<input id="event" type="text" required>

<label for="date">Tarehe ya tukio</label>
<input id="date" type="date" required>

<label for="quantity">Idadi ya tiketi</label>
<select id="quantity">
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
<option value="5">5</option>
<option value="10">10</option>
</select>

<label for="price">Bei ya tiketi moja (TSh)</label>
<input id="price" type="number" min="0" step="100" value="0" required>

<div class="total">
Bei ya tiketi moja: TSh <span id="unitPrice">0</span><br><br>
<strong>Jumla ya gharama: TSh <span id="total">0</span></strong>
</div>

<button type="submit">Wasilisha Ombi</button>
</form>
<p id="message" role="status"></p>
</section>
</main>
<footer>© WESTERN EAGLE ENTERTAINMENT MINISTRY</footer>
<script>
const quantity = document.getElementById("quantity");
const price = document.getElementById("price");

function calculateTotal(){
 const q = Number(quantity.value);
 const p = Number(price.value);
 document.getElementById("unitPrice").textContent =
  Math.max(0,p).toLocaleString("en-US");
 document.getElementById("total").textContent =
  (q * Math.max(0,p)).toLocaleString("en-US");
}
quantity.addEventListener("change",calculateTotal);
price.addEventListener("input",calculateTotal);
document.getElementById("ticketForm").addEventListener("submit",function(e){
 e.preventDefault();
 document.getElementById("message").textContent =
 "Ombi limejazwa kwenye ukurasa huu. Bado halijahifadhiwa kwenye mfumo wala kuthibitishwa kama tiketi.";
});
calculateTotal();
</script>
</body>
</html>
