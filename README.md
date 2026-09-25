<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>Shree Ram Janki Mandir Durga Puja Seva Samiti</title>

<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-database-compat.js"></script>

<style>
*{
  box-sizing:border-box;
}

body{
  margin:0;
  font-family:Arial,sans-serif;
  background:#f6f1e8;
  color:#222;
}

header{
  background:linear-gradient(135deg,#8b0000,#e65100);
  color:white;
  text-align:center;
  padding:28px 15px;
}

header h1{
  margin:0;
  font-size:25px;
}

header p{
  margin:8px 0 0;
}

.container{
  max-width:1050px;
  margin:auto;
  padding:18px;
}

.card{
  background:white;
  padding:20px;
  margin:15px 0;
  border-radius:15px;
  box-shadow:0 3px 12px #0002;
}

button{
  border:0;
  padding:12px 18px;
  border-radius:9px;
  cursor:pointer;
  font-weight:bold;
  margin:4px;
}

button:active{
  transform:scale(.98);
}

.primary{
  background:#e65100;
  color:white;
}

.green{
  background:#16803c;
  color:white;
}

.red{
  background:#c62828;
  color:white;
}

.dark{
  background:#333;
  color:white;
}

.gray{
  background:#777;
  color:white;
}

input,
textarea,
select{
  width:100%;
  padding:12px;
  margin:7px 0 14px;
  border:1px solid #ccc;
  border-radius:8px;
  font-size:15px;
  background:white;
}

input:focus,
textarea:focus,
select:focus{
  outline:none;
  border-color:#e65100;
}

textarea{
  min-height:100px;
  resize:vertical;
}

.hidden{
  display:none !important;
}

.center{
  text-align:center;
}

.nav{
  display:flex;
  flex-wrap:wrap;
  gap:8px;
  justify-content:center;
  padding:12px;
  background:white;
  position:sticky;
  top:0;
  z-index:100;
  box-shadow:0 2px 8px #0002;
}

.nav button{
  background:#8b0000;
  color:white;
}

.status{
  display:inline-block;
  padding:6px 11px;
  border-radius:20px;
  font-size:12px;
  font-weight:bold;
}

.pending{
  background:#fff3cd;
  color:#856404;
}

.accepted{
  background:#d4edda;
  color:#155724;
}

.rejected{
  background:#f8d7da;
  color:#721c24;
}

.item{
  border:1px solid #ddd;
  border-radius:10px;
  padding:15px;
  margin:10px 0;
  background:#fff;
}

.item h3{
  margin-top:0;
}

.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(170px,1fr));
  gap:12px;
}

.gallery-card{
  border:1px solid #ddd;
  border-radius:12px;
  overflow:hidden;
  background:white;
}

.gallery img{
  width:100%;
  height:180px;
  object-fit:cover;
  display:block;
}

.gallery-title{
  padding:10px;
  text-align:center;
  font-weight:bold;
}

.stats{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
  gap:10px;
  margin:10px 0 20px;
}

.stat{
  background:#fff;
  border-radius:12px;
  padding:16px;
  text-align:center;
  box-shadow:0 2px 8px #0001;
}

.stat-number{
  font-size:26px;
  font-weight:bold;
}

.success-box{
  background:#e8f5e9;
  border:1px solid #81c784;
  padding:15px;
  border-radius:10px;
  margin-top:15px;
}

.error-box{
  background:#ffebee;
  border:1px solid #ef9a9a;
  padding:15px;
  border-radius:10px;
  margin-top:15px;
}

.info-box{
  background:#e3f2fd;
  border:1px solid #90caf9;
  padding:15px;
  border-radius:10px;
  margin-top:15px;
}

.small{
  font-size:13px;
  color:#666;
}

footer{
  background:#222;
  color:white;
  text-align:center;
  padding:20px;
  margin-top:30px;
}

.connection{
  position:fixed;
  bottom:15px;
  right:15px;
  z-index:200;
  padding:8px 12px;
  border-radius:20px;
  font-size:12px;
  font-weight:bold;
  box-shadow:0 2px 8px #0003;
}

.online{
  background:#d4edda;
  color:#155724;
}

.offline{
  background:#f8d7da;
  color:#721c24;
}

@media(max-width:600px){

  header h1{
    font-size:20px;
  }

  .container{
    padding:10px;
  }

  .card{
    padding:15px;
  }

  .nav button{
    flex:1;
    min-width:80px;
    padding:10px 8px;
    font-size:13px;
  }

  button{
    padding:11px 13px;
  }

  .gallery img{
    height:150px;
  }
}
</style>
</head>

<body>

<header>
  <h1>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h1>
  <p>Siswa Bazar</p>
</header>

<div class="nav">
  <button onclick="showPage('home')">🏠 Home</button>
  <button onclick="showPage('join')">🤝 Join Us</button>
  <button onclick="showPage('news')">📰 News</button>
  <button onclick="showPage('gallery')">🖼️ Gallery</button>
  <button onclick="showPage('admin')">🔐 Admin</button>
</div>

<div class="container">

<!-- ================= HOME ================= -->

<section id="home">

  <div class="card center">
    <h2>जय श्री राम 🚩</h2>

    <p>
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति में आपका स्वागत है।
    </p>

    <button class="primary" onclick="showPage('join')">
      Join Committee / Volunteer
    </button>
  </div>

  <div class="card">
    <h2>🤝 हमसे जुड़ें</h2>

    <p>
      आप Volunteer या Committee Member के रूप में अपना विवरण भेज सकते हैं।
    </p>

    <button class="primary" onclick="showPage('join')">
      आवेदन करें
    </button>
  </div>

  <div class="card">
    <h2>📰 Latest News</h2>
    <div id="homeNews">
      Loading...
    </div>
  </div>

</section>


<!-- ================= JOIN ================= -->

<section id="join" class="hidden">

  <div class="card" id="joinChoice">

    <h2 class="center">
      आप किस रूप में जुड़ना चाहते हैं?
    </h2>

    <div class="center">

      <button
        class="primary"
        onclick="openForm('volunteer')">
        🙋 Volunteer
      </button>

      <button
        class="green"
        onclick="openForm('committee')">
        👥 Committee Member
      </button>

    </div>

  </div>


  <div class="card hidden" id="joinForm">

    <h2 id="formTitle"></h2>

    <form id="applicationForm"
          onsubmit="submitApplication(event)">

      <input type="hidden" id="memberType">

      <label>
        पूरा नाम *
      </label>

      <input
        id="name"
        maxlength="80"
        required
        placeholder="अपना पूरा नाम">


      <label>
        मोबाइल नंबर *
      </label>

      <input
        id="phone"
        type="tel"
        inputmode="numeric"
        maxlength="10"
        required
        placeholder="10 digit mobile number">


      <label>
        पता *
      </label>

      <textarea
        id="address"
        maxlength="300"
        required
        placeholder="पूरा पता"></textarea>


      <label>
        उम्र
      </label>

      <input
        id="age"
        type="number"
        min="1"
        max="100"
        placeholder="उम्र">


      <label>
        आप क्या योगदान देना चाहते हैं?
      </label>

      <textarea
        id="contribution"
        maxlength="500"
        placeholder="जैसे सेवा, व्यवस्था, प्रचार आदि"></textarea>


      <label>
        अन्य जानकारी
      </label>

      <textarea
        id="message"
        maxlength="500"
        placeholder="कोई अन्य जानकारी"></textarea>


      <button
        class="primary"
        type="submit">
        📤 Submit Application
      </button>

      <button
        type="button"
        onclick="backToChoice()">
        ← Back
      </button>

    </form>

  </div>


  <div id="submitMessage"></div>

</section>


<!-- ================= NEWS ================= -->

<section id="news" class="hidden">

  <div class="card">

    <h2>📰 Latest News</h2>

    <div id="newsList">
      Loading...
    </div>

  </div>

</section>


<!-- ================= GALLERY ================= -->

<section id="gallery" class="hidden">

  <div class="card">

    <h2>🖼️ Gallery</h2>

    <div
      class="gallery"
      id="galleryList">

      Loading...

    </div>

  </div>

</section>


<!-- ================= ADMIN ================= -->

<section id="admin" class="hidden">


  <!-- LOGIN -->

  <div
    class="card"
    id="adminLogin">

    <h2>🔐 Admin Login</h2>

    <p class="small">
      केवल अधिकृत समिति Admin के लिए।
    </p>

    <input
      type="password"
      id="adminPassword"
      placeholder="Admin Password"
      autocomplete="current-password"
      onkeydown="if(event.key==='Enter') adminLogin()">

    <button
      class="primary"
      onclick="adminLogin()">
      🔐 Login
    </button>

    <p id="loginMsg"></p>

  </div>


  <!-- ADMIN PANEL -->

  <div
    id="adminPanel"
    class="hidden">


    <div class="card">

      <h2>👑 Admin Panel</h2>

      <p>
        Welcome Admin
      </p>

      <button
        class="red"
        onclick="adminLogout()">
        Logout
      </button>

    </div>


    <!-- STATS -->

    <div class="stats">

      <div class="stat">
        <div class="stat-number"
             id="totalApplications">
          0
        </div>
        <div>Total</div>
      </div>

      <div class="stat">
        <div class="stat-number"
             id="pendingApplications">
          0
        </div>
        <div>Pending</div>
      </div>

      <div class="stat">
        <div class="stat-number"
             id="acceptedApplications">
          0
        </div>
        <div>Accepted</div>
      </div>

      <div class="stat">
        <div class="stat-number"
             id="rejectedApplications">
          0
        </div>
        <div>Rejected</div>
      </div>

    </div>


    <!-- APPLICATIONS -->

    <div class="card">

      <h2>📋 Applications</h2>

      <select
        id="filterStatus"
        onchange="renderApplications()">

        <option value="all">
          All Applications
        </option>

        <option value="pending">
          Pending
        </option>

        <option value="accepted">
          Accepted
        </option>

        <option value="rejected">
          Rejected
        </option>

      </select>


      <input
        id="applicationSearch"
        placeholder="🔎 Name या Mobile से search करें"
        oninput="renderApplications()">


      <div id="applications">
        Loading...
      </div>

    </div>


    <!-- ADD NEWS -->

    <div class="card">

      <h2>📰 Add News</h2>

      <input
        id="newsTitle"
        maxlength="150"
        placeholder="News Title">

      <textarea
        id="newsText"
        maxlength="1000"
        placeholder="News Details"></textarea>

      <button
        class="primary"
        onclick="addNews()">
        ➕ Add News
      </button>

      <div id="adminNews"></div>

    </div>


    <!-- GALLERY -->

    <div class="card">

      <h2>🖼️ Add Gallery Photo</h2>

      <input
        id="photoTitle"
        maxlength="100"
        placeholder="Photo Title">

      <input
        id="photoUrl"
        type="url"
        placeholder="Image URL">

      <p class="small">
        अभी Gallery में image URL इस्तेमाल हो रहा है।
      </p>

      <button
        class="primary"
        onclick="addPhoto()">
        ➕ Add Photo
      </button>

      <div id="adminGallery"></div>

    </div>


  </div>

</section>

</div>


<footer>

  <p>
    © 2026 Shree Ram Janki Mandir Durga Puja Seva Samiti
  </p>

  <p>
    जय श्री राम 🚩
  </p>

</footer>


<div
  id="connectionStatus"
  class="connection offline">
  Connecting...
</div>


<script>

/* =========================================================
   FIREBASE CONFIG
   ========================================================= */

const firebaseConfig = {

  apiKey: "PASTE_YOUR_API_KEY_HERE",

  authDomain:
  "shree-ram-janki-mandir-durga.firebaseapp.com",

  databaseURL:
  "https://shree-ram-janki-mandir-durga-default-rtdb.asia-southeast1.firebasedatabase.app",

  projectId:
  "shree-ram-janki-mandir-durga",

  storageBucket:
  "shree-ram-janki-mandir-durga.firebasestorage.app",

  messagingSenderId:
  "PASTE_YOUR_MESSAGING_SENDER_ID",

  appId:
  "PASTE_YOUR_APP_ID"

};


/* =========================================================
   FIREBASE INITIALIZATION
   ========================================================= */

let db = null;
let firebaseReady = false;

try {

  if(
    firebaseConfig.apiKey &&
    firebaseConfig.apiKey !== "PASTE_YOUR_API_KEY_HERE" &&
    firebaseConfig.messagingSenderId &&
    firebaseConfig.messagingSenderId !== "PASTE_YOUR_MESSAGING_SENDER_ID" &&
    firebaseConfig.appId &&
    firebaseConfig.appId !== "PASTE_YOUR_APP_ID"
  ){

    firebase.initializeApp(firebaseConfig);

    db = firebase.database();

    firebaseReady = true;

  }else{

    console.warn(
      "Firebase config incomplete."
    );

  }

}catch(error){

  console.error(error);

}


/* =========================================================
   ADMIN
   ========================================================= */

const ADMIN_PASSWORD = "123456";

let applicationsCache = {};

let listenersAttached = false;


/* =========================================================
   CONNECTION STATUS
   ========================================================= */

function updateConnectionStatus(){

  const el =
    document.getElementById("connectionStatus");

  if(!el) return;

  if(!firebaseReady){

    el.innerText =
      "Firebase Config Required";

    el.className =
      "connection offline";

    return;

  }

  db.ref(".info/connected")
    .on("value",snapshot=>{

      if(snapshot.val() === true){

        el.innerText = "● Online";
        el.className =
          "connection online";

      }else{

        el.innerText = "● Offline";
        el.className =
          "connection offline";

      }

    });

}


/* =========================================================
   FIREBASE CHECK
   ========================================================= */

function checkFirebase(){

  if(!firebaseReady){

    alert(
      "Firebase config incomplete hai.\n\n" +
      "apiKey, messagingSenderId aur appId " +
      "Firebase Console se add karein."
    );

    return false;

  }

  return true;

}


/* =========================================================
   PAGE SYSTEM
   ========================================================= */

function showPage(page){

  document
    .querySelectorAll("section")
    .forEach(section=>{
      section.classList.add("hidden");
    });

  const selected =
    document.getElementById(page);

  if(selected){
    selected.classList.remove("hidden");
  }

  if(page === "home"){
    loadHomeNews();
  }

  if(page === "news"){
    loadNews();
  }

  if(page === "gallery"){
    loadGallery();
  }

  if(
    page === "admin" &&
    sessionStorage.getItem("admin") === "yes"
  ){

    showAdminPanel();

  }

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


/* =========================================================
   JOIN FORM
   ========================================================= */

function openForm(type){

  document
    .getElementById("joinChoice")
    .classList.add("hidden");

  document
    .getElementById("joinForm")
    .classList.remove("hidden");

  document
    .getElementById("memberType")
    .value = type;

  document
    .getElementById("submitMessage")
    .innerHTML = "";

  if(type === "volunteer"){

    document
      .getElementById("formTitle")
      .innerText =
      "🙋 Volunteer Registration";

  }else{

    document
      .getElementById("formTitle")
      .innerText =
      "👥 Committee Member Registration";

  }

}


function backToChoice(){

  document
    .getElementById("joinForm")
    .classList.add("hidden");

  document
    .getElementById("joinChoice")
    .classList.remove("hidden");

  document
    .getElementById("submitMessage")
    .innerHTML = "";

}


/* =========================================================
   SUBMIT APPLICATION
   ========================================================= */

async function submitApplication(e){

  e.preventDefault();

  if(!checkFirebase()) return;

  const type =
    document.getElementById("memberType").value;

  const name =
    document.getElementById("name").value.trim();

  const phone =
    document.getElementById("phone").value.trim();

  const address =
    document.getElementById("address").value.trim();

  const age =
    document.getElementById("age").value.trim();

  const contribution =
    document
      .getElementById("contribution")
      .value.trim();

  const message =
    document
      .getElementById("message")
      .value.trim();


  if(!type){

    alert("Volunteer या Committee Member चुनें.");

    return;

  }


  if(name.length < 2){

    alert("कृपया सही नाम डालें.");

    return;

  }


  if(!/^[0-9]{10}$/.test(phone)){

    alert(
      "कृपया 10 digit mobile number डालें."
    );

    return;

  }


  const submitButton =
    document.querySelector(
      "#applicationForm button[type='submit']"
    );

  submitButton.disabled = true;
  submitButton.innerText =
    "Submitting...";


  const data = {

    type:type,

    name:name,

    phone:phone,

    address:address,

    age:age,

    contribution:contribution,

    message:message,

    status:"pending",

    createdAt:Date.now()

  };


  try{

    const newRef =
      await db
        .ref("applications")
        .push(data);

    const applicationId =
      newRef.key;


    document
      .getElementById("submitMessage")
      .innerHTML = `

      <div class="success-box">

        <h3>✅ Application Submitted</h3>

        <p>
          आपका application successfully submit हो गया है।
        </p>

        <p>
          Admin verification के बाद status update करेगा।
        </p>

        <p>
          <b>Application ID:</b>
          ${escapeHtml(applicationId)}
        </p>

        <p class="small">
          इस ID को संभालकर रखें।
        </p>

      </div>

      `;


    document
      .getElementById("applicationForm")
      .reset();


    document
      .getElementById("memberType")
      .value = type;


  }catch(error){

    console.error(error);

    document
      .getElementById("submitMessage")
      .innerHTML = `

      <div class="error-box">

        ❌ Application submit नहीं हो पाया।

        <br><br>

        ${escapeHtml(error.message)}

      </div>

      `;

  }finally{

    submitButton.disabled = false;

    submitButton.innerText =
      "📤 Submit Application";

  }

}


/* =========================================================
   ADMIN LOGIN
   ========================================================= */

function adminLogin(){

  const password =
    document
      .getElementById("adminPassword")
      .value;

  const msg =
    document.getElementById("loginMsg");


  if(password === ADMIN_PASSWORD){

    sessionStorage.setItem(
      "admin",
      "yes"
    );

    msg.innerText = "";

    showAdminPanel();

  }else{

    msg.innerText =
      "❌ Wrong password";

    msg.style.color =
      "#c62828";

  }

}


function showAdminPanel(){

  document
    .getElementById("adminLogin")
    .classList.add("hidden");

  document
    .getElementById("adminPanel")
    .classList.remove("hidden");


  if(!checkFirebase()) return;


  attachAdminListeners();

}


function adminLogout(){

  sessionStorage.removeItem("admin");

  document
    .getElementById("adminPanel")
    .classList.add("hidden");

  document
    .getElementById("adminLogin")
    .classList.remove("hidden");

  document
    .getElementById("adminPassword")
    .value = "";

  document
    .getElementById("loginMsg")
    .innerText = "";

}


/* =========================================================
   ADMIN LISTENERS
   ========================================================= */

function attachAdminListeners(){

  if(listenersAttached){

    renderApplications();

    return;

  }

  listenersAttached = true;


  db.ref("applications")
    .on("value",snapshot=>{

      applicationsCache = {};

      snapshot.forEach(child=>{

        applicationsCache[child.key] =
          {
            id:child.key,
            ...child.val()
          };

      });

      updateApplicationStats();

      renderApplications();

    });


  db.ref("news")
    .on("value",snapshot=>{

      renderAdminNews(snapshot);

   
