<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>World Explorer - 15 Countries</title>

<style>
:root {
  --bg: #eef3ff;
  --card: #ffffff;
  --text: #17223b;
  --primary: #315be8;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: var(--bg);
  color: var(--text);
}

header {
  background: linear-gradient(120deg, #13275b, #315be8);
  color: white;
  padding: 25px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}

header h1 { margin: 0; }

button {
  cursor: pointer;
  border: none;
  padding: 11px 15px;
  border-radius: 9px;
  font-weight: bold;
}

.admin-btn {
  background: white;
  color: #2446b4;
}

.container {
  max-width: 1150px;
  margin: 25px auto;
  padding: 0 15px;
}

.search {
  width: 100%;
  padding: 14px;
  border: 1px solid #ddd;
  border-radius: 10px;
  margin-bottom: 18px;
  font-size: 16px;
}

.layout {
  display: grid;
  grid-template-columns: 280px 1fr;
  gap: 18px;
}

.sidebar, .details {
  background: var(--card);
  border-radius: 15px;
  padding: 18px;
  box-shadow: 0 5px 20px #00000010;
}

.country-list {
  display: grid;
  gap: 7px;
}

.country-btn {
  text-align: left;
  background: transparent;
  color: var(--text);
  font-size: 15px;
}

.country-btn:hover, .country-btn.active {
  background: #eaf0ff;
  color: #2449c2;
}

.flag {
  font-size: 24px;
  margin-right: 9px;
}

.hero {
  display: flex;
  align-items: center;
  gap: 20px;
  border-bottom: 1px solid #ddd;
  padding-bottom: 18px;
}

.big-flag {
  font-size: 65px;
}

.hero h2 {
  margin: 0;
  font-size: 30px;
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 12px;
  margin-top: 20px;
}

.info {
  background: var(--bg);
  padding: 15px;
  border-radius: 11px;
  overflow-wrap: anywhere;
}

.info small {
  display: block;
  color: #66728a;
  font-weight: bold;
  margin-bottom: 6px;
}

.info strong {
  font-size: 16px;
}

h3 {
  margin-top: 25px;
}

.places {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
}

.place {
  background: var(--bg);
  padding: 13px;
  border-radius: 10px;
}

.about {
  background: var(--bg);
  padding: 14px;
  border-radius: 10px;
  line-height: 1.6;
}

.welcome {
  text-align: center;
  padding: 60px 10px;
  color: #66728a;
}

.modal {
  display: none;
  position: fixed;
  inset: 0;
  background: #0009;
  align-items: center;
  justify-content: center;
  padding: 15px;
}

.modal.show { display: flex; }

.dialog {
  background: var(--card);
  color: var(--text);
  padding: 25px;
  border-radius: 15px;
  width: 100%;
  max-width: 400px;
}

.dialog input, .dialog select {
  width: 100%;
  padding: 12px;
  margin: 8px 0;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.primary {
  background: var(--primary);
  color: white;
}

.secondary {
  background: #e8edf6;
  color: #17223b;
}

footer {
  text-align: center;
  padding: 25px;
  color: #66728a;
}

@media(max-width: 750px) {
  .layout { grid-template-columns: 1fr; }
  .info-grid, .places { grid-template-columns: 1fr; }
  .hero h2 { font-size: 23px; }
}
</style>
</head>

<body>

<header>
  <div>
    <h1>🌍 World Explorer</h1>
    <p>Explore 15 countries around the world</p>
  </div>
  <button class="admin-btn" onclick="openAdmin()">
    ⚙ Admin Panel
  </button>
</header>

<main class="container">

  <h2>Explore Countries</h2>
  <input
    class="search"
    id="search"
    placeholder="Search country..."
    oninput="renderCountries()"
  >

  <div class="layout">

    <aside class="sidebar">
      <h3>🌐 Select a Country</h3>
      <div class="country-list" id="countryList"></div>
    </aside>

    <section class="details" id="details">
      <div class="welcome">
        <div style="font-size:55px">🧭</div>
        <h2>Welcome to World Explorer</h2>
        <p>Select a country to see its complete information.</p>
      </div>
    </section>

  </div>
</main>

<footer>
  World Explorer | Offline Country Information Website
</footer>

<div class="modal" id="adminModal">
  <div class="dialog">
    <h2>⚙ Admin Panel</h2>

    <div id="loginArea">
      <p>Enter Admin PIN</p>
      <input type="password" id="pin" placeholder="Admin PIN">
      <button class="primary" onclick="login()">Login</button>
      <button class="secondary" onclick="closeAdmin()">Cancel</button>
      <p style="font-size:12px;color:gray">
        Demo PIN: 246810. This is not secure authentication.
      </p>
    </div>

    <div id="settingsArea" style="display:none">
      <p>Change Website Background</p>
      <select id="theme">
        <option value="blue">Light Blue</option>
        <option value="cream">Cream</option>
        <option value="mint">Mint Green</option>
        <option value="dark">Dark Mode</option>
      </select>

      <button class="primary" onclick="saveTheme()">Save</button>
      <button class="secondary" onclick="logout()">Logout</button>
      <button class="secondary" onclick="closeAdmin()">Close</button>
    </div>
  </div>
</div>

<script>

const countries = [

{
name:"India", flag:"🇮🇳",
capital:"New Delhi",
currency:"Indian Rupee (INR ₹)",
pm:"Narendra Modi",
president:"Droupadi Murmu",
cm:"Chief Ministers lead individual Indian states.",
government:"Federal Parliamentary Democratic Republic",
language:"Hindi and English; many regional languages",
about:"India is a South Asian country famous for its diverse cultures, historic monuments, traditions and landscapes.",
places:["Taj Mahal - Agra","Red Fort - Delhi","Jaipur City Palace","Varanasi Ghats","Gateway of India"]
},

{
name:"United States", flag:"🇺🇸",
capital:"Washington, D.C.",
currency:"US Dollar (USD $)",
pm:"No Prime Minister; President Donald Trump leads the executive branch.",
president:"Donald Trump",
cm:"States have Governors, not Chief Ministers.",
government:"Federal Presidential Republic",
language:"English is the most widely used.",
about:"The United States is a North American country known for its national parks, large cities and diverse landscapes.",
places:["Statue of Liberty","Grand Canyon","Golden Gate Bridge","Yellowstone National Park","Times Square"]
},

{
name:"United Kingdom", flag:"🇬🇧",
capital:"London",
currency:"Pound Sterling (GBP £)",
pm:"Keir Starmer",
president:"No President; King Charles III is the monarch.",
cm:"Devolved governments have their own leaders.",
government:"Constitutional Parliamentary Monarchy",
language:"English, Welsh and regional languages",
about:"The United Kingdom consists of England, Scotland, Wales and Northern Ireland.",
places:["Big Ben","Tower of London","Stonehenge","Edinburgh Castle","Giant's Causeway"]
},

{
name:"Canada", flag:"🇨🇦",
capital:"Ottawa",
currency:"Canadian Dollar (CAD $)",
pm:"Mark Carney",
president:"No President; King Charles III is monarch.",
cm:"Provinces are led by Premiers.",
government:"Federal Parliamentary Monarchy",
language:"English and French",
about:"Canada is famous for forests, lakes, mountains and multicultural cities.",
places:["Niagara Falls","Banff National Park","CN Tower","Old Quebec","Lake Louise"]
},

{
name:"Australia", flag:"🇦🇺",
capital:"Canberra",
currency:"Australian Dollar (AUD $)",
pm:"Anthony Albanese",
president:"No President; King Charles III is monarch.",
cm:"States have Premiers; some territories have Chief Ministers.",
government:"Federal Parliamentary Monarchy",
language:"English is most widely used.",
about:"Australia is a country and continent famous for beaches, wildlife and the Great Barrier Reef.",
places:["Sydney Opera House","Great Barrier Reef","Uluru","Great Ocean Road","Kakadu National Park"]
},

{
name:"France", flag:"🇫🇷",
capital:"Paris",
currency:"Euro (EUR €)",
pm:"Sébastien Lecornu",
president:"Emmanuel Macron",
cm:"No Chief Minister; France has a Prime Minister.",
government:"Semi-Presidential Republic",
language:"French",
about:"France is famous for art, fashion, architecture and beautiful cities.",
places:["Eiffel Tower","Louvre Museum","Palace of Versailles","Mont-Saint-Michel","French Riviera"]
},

{
name:"Germany", flag:"🇩🇪",
capital:"Berlin",
currency:"Euro (EUR €)",
pm:"Federal Chancellor Friedrich Merz",
president:"Frank-Walter Steinmeier",
cm:"German states have Minister-Presidents.",
government:"Federal Parliamentary Republic",
language:"German",
about:"Germany is known for engineering, castles, forests and historic cities.",
places:["Brandenburg Gate","Cologne Cathedral","Neuschwanstein Castle","Black Forest","Museum Island"]
},

{
name:"Japan", flag:"🇯🇵",
capital:"Tokyo",
currency:"Japanese Yen (JPY ¥)",
pm:"Sanae Takaichi",
president:"No President; Emperor Naruhito is monarch.",
cm:"Prefectures have governors.",
government:"Parliamentary Constitutional Monarchy",
language:"Japanese",
about:"Japan is an East Asian island country famous for technology, temples and traditional culture.",
places:["Mount Fuji","Fushimi Inari Shrine","Tokyo Skytree","Arashiyama Bamboo Grove","Himeji Castle"]
},

{
name:"China", flag:"🇨🇳",
capital:"Beijing",
currency:"Renminbi (CNY ¥)",
pm:"Premier Li Qiang",
president:"Xi Jinping",
cm:"Provincial governments have regional leaders.",
government:"Single-Party Socialist Republic",
language:"Mandarin Chinese",
about:"China is an East Asian country with ancient history and famous landmarks.",
places:["Great Wall of China","Forbidden City","Terracotta Army","The Bund","Li River"]
},

{
name:"Russia", flag:"🇷🇺",
capital:"Moscow",
currency:"Russian Ruble (RUB ₽)",
pm:"Mikhail Mishustin",
president:"Vladimir Putin",
cm:"Regions have governors or regional heads.",
government:"Federal Semi-Presidential Republic",
language:"Russian",
about:"Russia is the world's largest country by land area.",
places:["Red Square","Saint Basil's Cathedral","Lake Baikal","Hermitage Museum","Kazan Kremlin"]
},

{
name:"United Arab Emirates", flag:"🇦🇪",
capital:"Abu Dhabi",
currency:"UAE Dirham (AED)",
pm:"Mohammed bin Rashid Al Maktoum",
president:"Mohamed bin Zayed Al Nahyan",
cm:"The UAE is a federation of seven emirates.",
government:"Federal Elective Monarchy",
language:"Arabic and English",
about:"The UAE is famous for modern architecture, desert landscapes and cultural heritage.",
places:["Burj Khalifa","Sheikh Zayed Grand Mosque","Palm Jumeirah","Louvre Abu Dhabi","Hatta Mountains"]
},

{
name:"Singapore", flag:"🇸🇬",
capital:"Singapore",
currency:"Singapore Dollar (SGD $)",
pm:"Lawrence Wong",
president:"Tharman Shanmugaratnam",
cm:"Not applicable; Singapore is a city-state.",
government:"Parliamentary Republic",
language:"English, Malay, Mandarin and Tamil",
about:"Singapore is a modern island city-state known for its gardens and skyline.",
places:["Gardens by the Bay","Marina Bay Sands","Sentosa Island","Merlion Park","Singapore Botanic Gardens"]
},

{
name:"Nepal", flag:"🇳🇵",
capital:"Kathmandu",
currency:"Nepalese Rupee (NPR)",
pm:"Balendra Shah",
president:"Ram Chandra Paudel",
cm:"Nepal's provinces have Chief Ministers.",
government:"Federal Parliamentary Republic",
language:"Nepali and regional languages",
about:"Nepal is a Himalayan country famous for Mount Everest and historic temples.",
places:["Mount Everest","Pashupatinath Temple","Boudhanath Stupa","Pokhara","Lumbini"]
},

{
name:"Sri Lanka", flag:"🇱🇰",
capital:"Sri Jayawardenepura Kotte",
currency:"Sri Lankan Rupee (LKR)",
pm:"Harini Amarasuriya",
president:"Anura Kumara Dissanayake",
cm:"Sri Lanka has provincial governors.",
government:"Semi-Presidential Republic",
language:"Sinhala and Tamil",
about:"Sri Lanka is an island country famous for beaches, tea plantations and ancient heritage.",
places:["Sigiriya Rock","Temple of the Tooth","Galle Fort","Ella","Yala National Park"]
},

{
name:"Pakistan", flag:"🇵🇰",
capital:"Islamabad",
currency:"Pakistani Rupee (PKR)",
pm:"Shehbaz Sharif",
president:"Asif Ali Zardari",
cm:"Pakistan's provinces have Chief Ministers.",
government:"Federal Parliamentary Republic",
language:"Urdu and English; regional languages",
about:"Pakistan is a South Asian country known for mountains, historic cities and ancient archaeological sites.",
places:["Faisal Mosque","Badshahi Mosque","Hunza Valley","Mohenjo-daro","Shah Faisal Mosque"]
}

];

function renderCountries() {
  const query = document.getElementById("search").value.toLowerCase();
  const list = document.getElementById("countryList");
  list.innerHTML = "";

  countries
    .filter(c => c.name.toLowerCase().includes(query))
    .forEach(c => {
      const btn = document.createElement("button");
      btn.className = "country-btn";
      btn.innerHTML = `<span class="flag">${c.flag}</span>${c.name}`;
      btn.onclick = () => showCountry(c.name);
      list.appendChild(btn);
    });
}

function showCountry(name) {
  const c = countries.find(x => x.name === name);
  if (!c) return;

  document.getElementById("details").innerHTML = `
    <div class="hero">
      <div class="big-flag">${c.flag}</div>
      <div>
        <h2>${c.name}</h2>
        <p>Country Information</p>
      </div>
    </div>

    <div class="info-grid">

      <div class="info">
        <small>🏳 Flag Appearance</small>
        <strong>${c.flag} ${c.name}</strong>
      </div>

      <div class="info">
        <small>🏛 Capital</small>
        <strong>${c.capital}</strong>
      </div>

      <div class="info">
        <small>💰 Currency</small>
        <strong>${c.currency}</strong>
      </div>

      <div class="info">
        <small>👔 Prime Minister / Head of Government</small>
        <strong>${c.pm}</strong>
      </div>

      <div class="info">
        <small>👑 President / Head of State</small>
        <strong>${c.president}</strong>
      </div>

      <div class="info">
        <small>🏢 Chief Minister (CM)</small>
        <strong>${c.cm}</strong>
      </div>

      <div class="info">
        <small>🏛 Government</small>
        <strong>${c.government}</strong>
      </div>

      <div class="info">
        <small>🗣 Languages</small>
        <strong>${c.language}</strong>
      </div>

    </div>

    <h3>About ${c.name}</h3>
    <p class="about">${c.about}</p>

    <h3>📍 Famous Places</h3>
    <div class="places">
      ${c.places.map((p,i) =>
        `<div class="place">📌 ${i+1}. ${p}</div>`
      ).join("")}
    </div>
  `;
}

function openAdmin() {
  document.getElementById("adminModal").classList.add("show");
  document.getElementById("loginArea").style.display = "block";
  document.getElementById("settingsArea").style.display = "none";
}

function closeAdmin() {
  document.getElementById("adminModal").classList.remove("show");
}

function login() {
  if (document.getElementById("pin").value === "246810") {
    document.getElementById("loginArea").style.display = "none";
    document.getElementById("settingsArea").style.display = "block";
  } else {
    alert("Incorrect PIN!");
  }
}

function saveTheme() {
  const themes = {
    blue: ["#eef3ff","#ffffff","#17223b","#315be8"],
    cream: ["#fff6e8","#fffdf8","#3d2c1e","#b36b32"],
    mint: ["#e9f8f1","#ffffff","#17382b","#168765"],
    dark: ["#111827","#1f2937","#f3f4f6","#8ba5ff"]
  };

  const t = document.getElementById("theme").value;
  const v = themes[t];

  document.documentElement.style.setProperty("--bg", v[0]);
  document.documentElement.style.setProperty("--card", v[1]);
  document.documentElement.style.setProperty("--text", v[2]);
  document.documentElement.style.setProperty("--primary", v[3]);

  try {
    localStorage.setItem("worldExplorerTheme", t);
  } catch(e) {}

  alert("Background changed successfully!");
}

function logout() {
  document.getElementById("settingsArea").style.display = "none";
  document.getElementById("loginArea").style.display = "block";
  document.getElementById("pin").value = "";
}

try {
  const saved = localStorage.getItem("worldExplorerTheme");
  if (saved) {
    document.getElementById("theme").value = saved;
    document.getElementById("theme").dispatchEvent(new Event("change"));
    const themes = {
      blue:["#eef3ff","#ffffff","#17223b","#315be8"],
      cream:["#fff6e8","#fffdf8","#3d2c1e","#b36b32"],
      mint:["#e9f8f1","#ffffff","#17382b","#168765"],
      dark:["#111827","#1f2937","#f3f4f6","#8ba5ff"]
    };
    const v=themes[saved];
    if(v) {
      document.documentElement.style.setProperty("--bg",v[0]);
      document.documentElement.style.setProperty("--card",v[1]);
      document.documentElement.style.setProperty("--text",v[2]);
      document.documentElement.style.setProperty("--primary",v[3]);
    }
  }
} catch(e) {}

renderCountries();

</script>
</body>
</html>
