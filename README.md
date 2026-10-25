
<!DOCTYPE html>
<html lang="sw">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WESTERN EAGLE TICKETING</title>
<style>
*{box-sizing:border-box}
body{margin:0;font-family:Arial,sans-serif;background:#f2f5f9;color:#172033}
header{background:#102b55;color:white;text-align:center;padding:25px 15px}
main{max-width:700px;margin:25px auto;padding:0 15px}
.card{background:white;padding:24px;border-radius:12px;box-shadow:0 3px 15px #0001}
label{display:block;margin-top:15px;font-weight:bold}
input,select{width:100%;padding:12px;margin-top:7px;border:1px solid #ccd3df;border-radius:6px;font-size:16px}
.summary{margin-top:20px;padding:16px;background:#eef4ff;border-radius:8px;line-height:1.8}
button{width:100%;padding:14px;margin-top:22px;background:#e4a629;border:0;border-radius:6px;font-weight:bold;font-size:16px;cursor:pointer}
.note{font-size:13px;color:#596579}
footer{text-align:center;padding:25px;color:#566176}
</style>
</head>
<body>
<header>
<h1>WESTERN EAGLE</h1>
<p>ENTERTAINMENT MINISTRY</p>
<h2>MFUMO WA TIKETI</h2>
<p>Karibu kwenye mfumo wa kuomba tiketi</p>
</header>
<main>
<section class="card">
<h2>Fomu ya Kuomba Tiketi</h2>
<form id="ticketForm">
<label for="name">Jina kamili la mteja</label>
<input id="name" required>

<label for="phone">Namba ya simu</label>
<input id="phone" type="tel" required>

<label for="event">Jina la tukio</label>
<input id="event" required>

<label for="date">Tarehe ya tukio</label>
<input id="date" type="date" required>

<label for="ticketType">Chagua aina ya tiketi</label>
<select id="ticketType" required>
<option value="table">Meza — TSh 150,000 (watu 3)</option>
<option value="vvip">VVIP — TSh 50,000 kwa mtu</option>
<option value="vip">VIP — TSh 25,000 kwa mtu</option>
<option value="general">Mzunguko wa kawaida — TSh 5,000</option>
<option value="food">Mzunguko wenye chakula — TSh 10,000</option>
</select>

<label for="quantity" id="quantityLabel">Idadi ya tiketi</label>
<input id="quantity" type="number" min="1" step="1" value="1" required>

<div class="summary" aria-live="polite">
<div>Bei ya tiketi/meza moja: <strong id="unitPrice">TSh 150,000</strong></div>
<div>Chakula na vinywaji: <strong id="foodInfo">Vimejumuishwa</strong></div>
<div>Uwezo wa nafasi uliopangwa: <strong id="capacity">Meza 300</strong></div>
<hr>
<div>Idadi ya watu: <strong id="people">3</strong></div>
<div>Jumla ya gharama: <strong id="total">TSh 150,000</strong></div>
</div>

<p class="note">Hii ni hesabu ya gharama ya awali. Ombi halijahifadhiwa wala kuthibitishwa kama tiketi.</p>
<button type="submit">Wasilisha Ombi</button>
</form>
<p id="message" role="status"></p>
</section>
</main>
<footer>© WESTERN EAGLE ENTERTAINMENT MINISTRY</footer>
<script>
const type=document.getElementById("ticketType");
const qty=document.getElementById("quantity");
const prices={table:150000,vvip:50000,vip:25000,general:5000,food:10000};
const capacities={table:300,vvip:400,vip:700,general:3000,food:3000};

function money(n){return "TSh "+n.toLocaleString("en-US");}

function updateSummary(){
 const t=type.value;
 const q=Math.max(1,Math.floor(Number(qty.value)||1));
 qty.value=q;
 const p=prices[t];
 const isTable=t==="table";
 document.getElementById("quantityLabel").textContent=
   isTable?"Idadi ya meza (meza moja ni watu 3)":"Idadi ya tiketi";
 document.getElementById("unitPrice").textContent=money(p);
 document.getElementById("foodInfo").textContent=
   ["table","vvip","vip","food"].includes(t)?"Vimejumuishwa":"Havijajumuishwa";
 document.getElementById("capacity").textContent=
   isTable?"Meza 300":capacities[t].toLocaleString("en-US")+" nafasi";
 document.getElementById("people").textContent=
   (isTable?q*3:q).toLocaleString("en-US");
 document.getElementById("total").textContent=money(q*p);
}

type.addEventListener("change",updateSummary);
qty.addEventListener("input",updateSummary);
document.getElementById("ticketForm").addEventListener("submit",function(e){
 e.preventDefault();
 document.getElementById("message").textContent=
 "Fomu imekaguliwa kwenye ukurasa huu. Ombi bado halijahifadhiwa kwenye mfumo; tiketi haijatolewa.";
});
updateSummary();
</script>
</body>
</html>
