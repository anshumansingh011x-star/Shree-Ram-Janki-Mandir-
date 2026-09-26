<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</title>

<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-database-compat.js"></script>

<style>
*{
  box-sizing:border-box;
}

html{
  scroll-behavior:smooth;
}

body{
  margin:0;
  font-family:Arial,"Noto Sans Devanagari",sans-serif;
  background:
    radial-gradient(circle at top,#fff4d6 0,#fff8ed 35%,#f8eee2 100%);
  color:#2b1608;
}

/* ================= HEADER ================= */

header{
  position:relative;
  overflow:hidden;
  text-align:center;
  color:white;
  padding:42px 15px 38px;
  background:
    linear-gradient(135deg,#5b0000,#8d1600 45%,#ed7600);
  box-shadow:0 5px 20px rgba(91,0,0,.3);
}

header:before,
header:after{
  content:"✦";
  position:absolute;
  font-size:90px;
  opacity:.08;
}

header:before{
  left:5%;
  top:-15px;
}

header:after{
  right:5%;
  bottom:-25px;
}

.om{
  font-size:45px;
  margin-bottom:8px;
}

header h1{
  margin:0;
  font-size:27px;
  line-height:1.4;
  text-shadow:0 3px 8px #400000;
}

header p{
  margin:9px 0;
  font-size:17px;
}

.headerLine{
  width:150px;
  height:3px;
  margin:14px auto;
  background:#ffd76a;
  border-radius:20px;
}

.jai{
  font-size:21px;
  font-weight:bold;
}

/* ================= NAV ================= */

nav{
  position:sticky;
  top:0;
  z-index:100;
  display:flex;
  flex-wrap:wrap;
  justify-content:center;
  gap:7px;
  padding:10px;
  background:rgba(255,255,255,.96);
  backdrop-filter:blur(10px);
  box-shadow:0 3px 15px rgba(0,0,0,.13);
}

nav button{
  border:0;
  padding:9px 14px;
  border-radius:25px;
  background:#7d0808;
  color:white;
  cursor:pointer;
  font-weight:bold;
  transition:.2s;
}

nav button:hover{
  transform:translateY(-2px);
  background:#b12b00;
}

/* ================= SECTIONS ================= */

section{
  max-width:1100px;
  margin:auto;
  padding:32px 15px;
}

.sectionTitle{
  text-align:center;
  margin-bottom:25px;
}

.sectionTitle h2{
  color:#810b00;
  margin-bottom:7px;
  font-size:27px;
}

.sectionTitle p{
  color:#765b4b;
}

/* ================= HERO ================= */

.hero{
  position:relative;
  overflow:hidden;
  text-align:center;
  padding:45px 20px;
  border-radius:25px;
  color:white;
  background:
    linear-gradient(135deg,rgba(89,0,0,.95),rgba(190,61,0,.92)),
    radial-gradient(circle,#ffbd4a,#7d0000);
  box-shadow:0 8px 30px rgba(100,0,0,.25);
}

.hero:before{
  content:"🚩";
  position:absolute;
  font-size:100px;
  left:-15px;
  top:-20px;
  opacity:.12;
}

.hero:after{
  content:"ॐ";
  position:absolute;
  font-size:130px;
  right:-15px;
  bottom:-40px;
  opacity:.1;
}

.hero h2{
  color:#ffd76a;
  font-size:31px;
  margin:5px 0 15px;
}

.hero p{
  max-width:750px;
  margin:auto;
  font-size:17px;
  line-height:1.8;
}

.heroJai{
  margin-top:18px;
  font-size:23px;
  font-weight:bold;
}

/* ================= CARDS ================= */

.card{
  background:rgba(255,255,255,.96);
  border:1px solid #f0d8b7;
  border-radius:18px;
  padding:20px;
  margin:16px 0;
  box-shadow:0 5px 20px rgba(90,35,0,.09);
}

.card h3{
  color:#7d0808;
}

.infoGrid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(210px,1fr));
  gap:15px;
  margin-top:20px;
}

.infoBox{
  text-align:center;
  padding:23px 15px;
  border-radius:18px;
  background:linear-gradient(145deg,#fff,#fff0d2);
  border:1px solid #efd1a5;
  box-shadow:0 4px 14px rgba(100,40,0,.08);
}

.infoIcon{
  font-size:36px;
}

/* ================= FORMS ================= */

input,
textarea,
select{
  width:100%;
  padding:13px;
  margin:6px 0 13px;
  border:1px solid #d9c3ae;
  border-radius:10px;
  background:#fffdf9;
  font-size:15px;
  outline:none;
}

input:focus,
textarea:focus,
select:focus{
  border-color:#a82a00;
  box-shadow:0 0 0 3px rgba(168,42,0,.08);
}

textarea{
  min-height:110px;
  resize:vertical;
}

button.main{
  border:0;
  padding:11px 17px;
  border-radius:9px;
  color:white;
  background:#850900;
  font-weight:bold;
  cursor:pointer;
  transition:.2s;
}

button.main:hover{
  transform:translateY(-1px);
  box-shadow:0 4px 10px rgba(100,0,0,.2);
}

button.green{
  background:#16803c;
}

button.red{
  background:#b00020;
}

button.orange{
  background:#df7000;
}

button.gray{
  background:#555;
}

.actions{
  display:flex;
  flex-wrap:wrap;
  gap:7px;
  margin-top:12px;
}

.actions button{
  border:0;
  color:white;
  padding:8px 11px;
  border-radius:7px;
  cursor:pointer;
}

/* ================= NEWS ================= */

.news{
  border-left:5px solid #d65c00;
}

.news h3{
  margin-top:0;
}

.newsDate{
  color:#8b7567;
  font-size:12px;
  margin-bottom:10px;
}

.readBtn{
  margin-top:8px;
}

.small{
  color:#76665c;
  font-size:13px;
}

.loading{
  text-align:center;
  padding:25px;
  color:#777;
}

/* ================= GALLERY ================= */

.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(210px,1fr));
  gap:17px;
}

.galleryItem{
  overflow:hidden;
  background:white;
  border-radius:16px;
  border:1px solid #ead6c0;
  box-shadow:0 5px 18px rgba(70,30,0,.12);
  transition:.25s;
}

.galleryItem:hover{
  transform:translateY(-4px);
}

.galleryItem img{
  width:100%;
  height:205px;
  display:block;
  object-fit:cover;
}

.galleryCaption{
  padding:12px;
  font-weight:bold;
  color:#6d0a00;
}

/* ================= APPLICATION ================= */

.formHeading{
  display:flex;
  align-items:center;
  gap:10px;
  color:#7d0808;
}

.formHeading span{
  font-size:30px;
}

/* ================= STATUS ================= */

.status{
  display:inline-block;
  padding:5px 10px;
  border-radius:20px;
  font-size:12px;
  font-weight:bold;
}

.pending{
  background:#fff0b3;
  color:#795600;
}

.accepted{
  background:#c7f5d5;
  color:#08752e;
}

.rejected{
  background:#ffd0d5;
  color:#9b0016;
}

/* ================= ADMIN ================= */

.adminPanel{
  display:none;
}

.adminTop{
  background:linear-gradient(135deg,#350000,#780700);
  color:white;
}

.adminTop h3{
  color:#ffd76a;
}

.filterGrid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:10px;
}

.applicationCard{
  border-left:5px solid #9b2300;
}

/* ================= MODAL ================= */

.modal{
  display:none;
  position:fixed;
  inset:0;
  z-index:1000;
  background:rgba(0,0,0,.75);
  padding:20px;
  overflow:auto;
}

.modalBox{
  max-width:750px;
  margin:35px auto;
  background:white;
  border-radius:18px;
  padding:25px;
  box-shadow:0 10px 40px rgba(0,0,0,.35);
}

.modalBox h2{
  color:#810b00;
}

/* ================= FOOTER ================= */

footer{
  position:relative;
  overflow:hidden;
  text-align:center;
  color:white;
  padding:32px 15px;
  background:linear-gradient(135deg,#470000,#800900);
  margin-top:25px;
}

footer .omFooter{
  font-size:35px;
  color:#ffd76a;
}

/* ================= MOBILE ================= */

@media(max-width:600px){

  header h1{
    font-size:21px;
  }

  .om{
    font-size:38px;
  }

  nav button{
    font-size:12px;
    padding:8px 10px;
  }

  section{
    padding:25px 10px;
  }

  .hero{
    padding:35px 15px;
  }

  .hero h2{
    font-size:25px;
  }

  .filterGrid{
    grid-template-columns:1fr;
  }
}
</style>
</head>

<body>

<!-- ================= HEADER ================= -->

<header>

  <div class="om">ॐ</div>

  <h1>
    श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति
  </h1>

  <div class="headerLine"></div>

  <p>📍 Siswa Bazar</p>

  <div class="jai">
    जय श्री राम 🚩
  </div>

</header>


<!-- ================= NAV ================= -->

<nav>

  <button onclick="goTo('home')">🏠 Home</button>
  <button onclick="goTo('news')">📰 News</button>
  <button onclick="goTo('gallery')">🖼️ Gallery</button>
  <button onclick="goTo('volunteer')">🙋 Volunteer</button>
  <button onclick="goTo('committee')">👥 Committee</button>
  <button onclick="goTo('admin')">🔐 Admin</button>

</nav>


<!-- ================= HOME ================= -->

<section id="home">

  <div class="hero">

    <h2>🙏 हार्दिक स्वागत है 🙏</h2>

    <p>
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति,
      Siswa Bazar की आधिकारिक वेबसाइट पर
      आपका हार्दिक स्वागत है।
    </p>

    <div class="heroJai">
      श्री राम जानकी मंदिर 🚩
    </div>

  </div>


  <div class="infoGrid">

    <div class="infoBox">
      <div class="infoIcon">📰</div>
      <h3>News & Updates</h3>
      <p>समिति की महत्वपूर्ण खबरें और अपडेट।</p>
    </div>

    <div class="infoBox">
      <div class="infoIcon">🖼️</div>
      <h3>Gallery</h3>
      <p>मंदिर एवं समिति से जुड़ी तस्वीरें।</p>
    </div>

    <div class="infoBox">
      <div class="infoIcon">🙋</div>
      <h3>Volunteer</h3>
      <p>सेवा कार्य में जुड़ने के लिए आवेदन करें।</p>
    </div>

    <div class="infoBox">
      <div class="infoIcon">👥</div>
      <h3>Committee</h3>
      <p>समिति से जुड़ने के लिए आवेदन करें।</p>
    </div>

  </div>

</section>


<!-- ================= NEWS ================= -->

<section id="news">

  <div class="sectionTitle">

    <h2>📰 News & Updates</h2>

    <p>
      समिति की ताजा खबरें और महत्वपूर्ण सूचनाएं
    </p>

  </div>

  <div id="newsList">

    <div class="loading">
      News loading...
    </div>

  </div>

</section>


<!-- ================= GALLERY ================= -->

<section id="gallery">

  <div class="sectionTitle">

    <h2>🖼️ Gallery</h2>

    <p>
      मंदिर एवं धार्मिक कार्यक्रमों की झलक
    </p>

  </div>

  <div class="card">

    <div id="galleryList" class="gallery">

      <div class="loading">
        Gallery loading...
      </div>

    </div>

  </div>

</section>


<!-- ================= VOLUNTEER ================= -->

<section id="volunteer">

  <div class="sectionTitle">

    <h2>🙋 Volunteer Application</h2>

    <p>
      सेवा कार्य में सहयोग करने के इच्छुक सदस्य
      यहाँ आवेदन कर सकते हैं।
    </p>

  </div>


  <div class="card">

    <div class="formHeading">
      <span>🚩</span>
      <h3>Volunteer Form</h3>
    </div>

    <form id="volunteerForm">

      <input
        id="vName"
        placeholder="पूरा नाम"
        required>

      <input
        id="vMobile"
        type="tel"
        maxlength="10"
        inputmode="numeric"
        placeholder="10 Digit Mobile Number"
        required>

      <input
        id="vAge"
        type="number"
        min="10"
        max="100"
        placeholder="Age"
        required>

      <textarea
        id="vAddress"
        placeholder="पूरा पता"
        required></textarea>

      <input
        id="vContribution"
        placeholder="आप किस प्रकार सहयोग करना चाहते हैं?">

      <input
        id="vPhoto"
        placeholder="Photo URL (optional)">

      <input
        id="vPdf"
        placeholder="Application PDF / Drive Link (optional)">

      <textarea
        id="vMessage"
        placeholder="अन्य जानकारी / संदेश"></textarea>

      <button
        type="submit"
        class="main">

        🚩 Submit Volunteer Application

      </button>

      <p
        id="vStatus"
        class="small">
      </p>

    </form>

  </div>

</section>


<!-- ================= COMMITTEE ================= -->

<section id="committee">

  <div class="sectionTitle">

    <h2>👥 Committee Application</h2>

    <p>
      समिति का हिस्सा बनने के लिए आवेदन करें।
    </p>

  </div>


  <div class="card">

    <div class="formHeading">
      <span>🛕</span>
      <h3>Committee Member Form</h3>
    </div>

    <form id="committeeForm">

      <input
        id="cName"
        placeholder="पूरा नाम"
        required>

      <input
        id="cMobile"
        type="tel"
        maxlength="10"
        inputmode="numeric"
        placeholder="10 Digit Mobile Number"
        required>

      <input
        id="cAge"
        type="number"
        min="10"
        max="100"
        placeholder="Age"
        required>

      <textarea
        id="cAddress"
        placeholder="पूरा पता"
        required></textarea>

      <input
        id="cContribution"
        placeholder="योगदान / जिम्मेदारी">

      <input
        id="cPhoto"
        placeholder="Photo URL (optional)">

      <textarea
        id="cMessage"
        placeholder="अन्य जानकारी / संदेश"></textarea>

      <button
        type="submit"
        class="main">

        🚩 Submit Committee Application

      </button>

      <p
        id="cStatus"
        class="small">
      </p>

    </form>

  </div>

</section>


<!-- ================= ADMIN ================= -->

<section id="admin">

  <div class="sectionTitle">

    <h2>🔐 Admin Panel</h2>

    <p>
      केवल अधिकृत समिति Admin के लिए
    </p>

  </div>


  <!-- LOGIN -->

  <div
    class="card"
    id="loginBox">

    <h3>🔑 Admin Login</h3>

    <input
      id="adminPassword"
      type="password"
      placeholder="Admin Password">

    <button
      class="main"
      onclick="adminLogin()">

      Login

    </button>

    <p
      id="loginStatus"
      class="small">
    </p>

  </div>


  <!-- ADMIN PANEL -->

  <div
    id="adminPanel"
    class="adminPanel">


    <!-- ADMIN HEADER -->

    <div class="card adminTop">

      <h3>🚩 Welcome Admin</h3>

      <p>
        यहाँ से applications, news और gallery manage करें।
      </p>

    </div>


    <!-- APPLICATIONS -->

    <div class="card">

      <h3>📋 Applications</h3>

      <div class="filterGrid">

        <select
          id="statusFilter"
          onchange="renderApplications()">

          <option value="all">All Applications</option>
          <option value="pending">Pending</option>
          <option value="accepted">Accepted</option>
          <option value="rejected">Rejected</option>

        </select>

        <input
          id="applicationSearch"
          oninput="renderApplications()"
          placeholder="🔎 Search Name / Mobile">

      </div>

      <div id="applicationsList"></div>

    </div>


    <!-- ADD NEWS -->

    <div class="card">

      <h3>📰 Add News</h3>

      <input
        id="newsTitle"
        maxlength="150"
        placeholder="News Title">

      <textarea
        id="newsDetails"
        maxlength="1000"
        placeholder="News Details"></textarea>

      <button
        class="main"
        onclick="addNews()">

        ➕ Add News

      </button>

    </div>


    <!-- ADD GALLERY -->

    <div class="card">

      <h3>🖼️ Add Gallery Photo</h3>

      <p class="small">
        Firebase Storage/Cloudinary के बिना
        direct image URL से photo add करें।
      </p>

      <input
        id="galleryTitle"
        placeholder="Photo Title">

      <input
        id="galleryUrl"
        placeholder="Image URL">

      <button
        class="main"
        onclick="addGallery()">

        ➕ Add Photo

      </button>

      <p
        id="galleryStatus"
        class="small">
      </p>

    </div>


    <button
      class="main red"
      onclick="adminLogout()">

      🔒 Logout

    </button>

  </div>

</section>


<!-- ================= NEWS MODAL ================= -->

<div
  class="modal"
  id="newsModal">

  <div class="modalBox">

    <h2 id="modalTitle"></h2>

    <p
      id="modalDetails"
      style="white-space:pre-wrap;line-height:1.7">
    </p>

    <button
      class="main"
      onclick="closeNews()">

      Close

    </button>

  </div>

</div>


<!-- ================= FOOTER ================= -->

<footer>

  <div class="omFooter">ॐ</div>

  <b>
    श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति
  </b>

  <br>

  Siswa Bazar

  <br><br>

  जय श्री राम 🚩

  <br><br>

  <span style="font-size:12px;opacity:.8">
    सेवा • श्रद्धा • समर्पण
  </span>

</footer>


<script>

/* =========================================================
   FIREBASE
========================================================= */

const firebaseConfig = {

  apiKey:
    "AIzaSyDLonsbRwdlq3Ru4NIvhFqLzjKEUaPnzfc",

  authDomain:
    "shree-ram-janki-mandir-durga.firebaseapp.com",

  databaseURL:
    "https://shree-ram-janki-mandir-durga-default-rtdb.asia-southeast1.firebasedatabase.app",

  projectId:
    "shree-ram-janki-mandir-durga",

  storageBucket:
    "shree-ram-janki-mandir-durga.firebasestorage.app",

  messagingSenderId:
    "603852207772",

  appId:
    "1:603852207772:web:a27f2828d95284a4c69f59",

  measurementId:
    "G-9QQJJEMH1V"

};

firebase.initializeApp(firebaseConfig);

const db=firebase.database();


/* =========================================================
   VARIABLES
========================================================= */

const ADMIN_PASSWORD="SRJM2026";

let isAdmin=false;

let applications={};

let newsData={};

let galleryData={};


/* =========================================================
   NAVIGATION
========================================================= */

function goTo(id){

  document
    .getElementById(id)
    .scrollIntoView({
      behavior:"smooth"
    });

}


/* =========================================================
   ADMIN LOGIN
========================================================= */

function adminLogin(){

  const password=
    document
      .getElementById("adminPassword")
      .value;

  if(password===ADMIN_PASSWORD){

    isAdmin=true;

    document
      .getElementById("loginBox")
      .style.display="none";

    document
      .getElementById("adminPanel")
      .style.display="block";

    renderApplications();
    renderNews();
    renderGallery();

  }else{

    document
      .getElementById("loginStatus")
      .innerText=
      "❌ Wrong admin password.";

  }

}


function adminLogout(){

  isAdmin=false;

  document
    .getElementById("loginBox")
    .style.display="block";

  document
    .getElementById("adminPanel")
    .style.display="none";

  document
    .getElementById("adminPassword")
    .value="";

  renderNews();
  renderGallery();

}


/* =========================================================
   VOLUNTEER
========================================================= */

document
.getElementById("volunteerForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const status=
    document.getElementById("vStatus");

  const mobile=
    document.getElementById("vMobile")
    .value.trim();

  if(!/^[0-9]{10}$/.test(mobile)){

    status.innerText=
      "❌ Mobile number 10 digit ka hona chahiye.";

    return;

  }

  try{

    const ref=
      db.ref("applications").push();

    await ref.set({

      type:"volunteer",

      name:
        document.getElementById("vName")
        .value.trim(),

      mobile:mobile,

      age:
        document.getElementById("vAge")
        .value,

      address:
        document.getElementById("vAddress")
        .value.trim(),

      contribution:
        document.getElementById("vContribution")
        .value.trim(),

      photo:
        document.getElementById("vPhoto")
        .value.trim(),

      pdfLink:
        document.getElementById("vPdf")
        .value.trim(),

      message:
        document.getElementById("vMessage")
        .value.trim(),

      status:"pending",

      createdAt:
        firebase.database.ServerValue.TIMESTAMP

    });

    document
      .getElementById("volunteerForm")
      .reset();

    status.innerText=
      "✅ Volunteer application successfully submit ho gayi.";

  }catch(error){

    console.error(error);

    status.innerText=
      "❌ Application submit nahi hui.";

  }

});


/* =========================================================
   COMMITTEE
========================================================= */

document
.getElementById("committeeForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const status=
    document.getElementById("cStatus");

  const mobile=
    document.getElementById("cMobile")
    .value.trim();

  if(!/^[0-9]{10}$/.test(mobile)){

    status.innerText=
      "❌ Mobile number 10 digit ka hona chahiye.";

    return;

  }

  try{

    const ref=
      db.ref("applications").push();

    await ref.set({

      type:"committee",

      name:
        document.getElementById("cName")
        .value.trim(),

      mobile:mobile,

      age:
        document.getElementById("cAge")
        .value,

      address:
        document.getElementById("cAddress")
        .value.trim(),

      contribution:
        document.getElementById("cContribution")
        .value.trim(),

      photo:
        document.getElementById("cPhoto")
        .value.trim(),

      pdfLink:"",

      message:
        document.getElementById("cMessage")
        .value.trim(),

      status:"pending",

      createdAt:
        firebase.database.ServerValue.TIMESTAMP

    });

    document
      .getElementById("committeeForm")
      .reset();

    status.innerText=
      "✅ Committee application successfully submit ho gayi.";

  }catch(error){

    console.error(error);

    status.innerText=
      "❌ Application submit nahi hui.";

  }

});


/* =========================================================
   APPLICATION LISTENER
========================================================= */

db.ref("applications").on("value",snapshot=>{

  applications=
    snapshot.val() || {};

  if(isAdmin){
    renderApplications();
  }

});


/* =========================================================
   RENDER APPLICATIONS
========================================================= */

function renderApplications(){

  const box=
    document.getElementById(
      "applicationsList"
    );

  if(!box)return;

  const filter=
    document.getElementById(
      "statusFilter"
    ).value;

  const search=
    document.getElementById(
      "applicationSearch"
    ).value
    .toLowerCase()
    .trim();

  let html="";

  Object
  .entries(applications)
  .sort((a,b)=>
    (b[1].createdAt||0)-
    (a[1].createdAt||0)
  )
  .forEach(([key,item])=>{

    const name=
      String(item.name||"");

    const mobile=
      String(item.mobile||"");

    const status=
      item.status||"pending";

    if(
      filter!=="all" &&
      status!==filter
    )return;

    if(
      search &&
      !name.toLowerCase().includes(search) &&
      !mobile.includes(search)
    )return;

    const type=
      item.type==="committee"
      ? "👥 Committee Member"
      : "🙋 Volunteer";

    html+=`

      <div class="card applicationCard">

        <h3>
          ${escapeHTML(name)}
        </h3>

        <p>
          <b>Application:</b>
          ${type}
        </p>

        <p>
          <b>📱 Mobile:</b>
          ${escapeHTML(mobile)}
        </p>

        <p>
          <b>Age:</b>
          ${escapeHTML(item.age||"")}
        </p>

        <p>
          <b>Address:</b>
          ${escapeHTML(item.address||"")}
        </p>

        <p>
          <b>Contribution:</b>
          ${escapeHTML(item.contribution||"")}
        </p>

        <p>
          <b>Message:</b>
          ${escapeHTML(item.message||"")}
        </p>

        <span class="status ${status}">
          ${status.toUpperCase()}
        </span>

        ${
          item.photo
          ?`
          <p>
            📷
            <a
              href="${safeURL(item.photo)}"
              target="_blank"
              rel="noopener">
              View Photo
            </a>
          </p>
          `
          :""
        }

        ${
          item.pdfLink
          ?`
          <p>
            📄
            <a
              href="${safeURL(item.pdfLink)}"
              target="_blank"
              rel="noopener">
              View Application PDF
            </a>
          </p>
          `
          :""
        }

        <div class="actions">

          <button
            class="green"
            onclick="changeStatus('${key}','accepted')">
            ✅ Accept
          </button>

          <button
            class="red"
            onclick="changeStatus('${key}','rejected')">
            ❌ Reject
          </button>

          <button
            class="gray"
            onclick="deleteApplication('${key}')">
            🗑️ Delete
          </button>

        </div>

      </div>

    `;

  });

  if(!html){

    html=`
      <div class="card">
        <b>कोई application नहीं मिली।</b>
      </div>
    `;

  }

  box.innerHTML=html;

}


/* =========================================================
   ACCEPT / REJECT
========================================================= */

function changeStatus(key,status){

  if(!isAdmin)return;

  db.ref("applications/"+key)
    .update({
      status:status
    });

}


/* =========================================================
   DELETE APPLICATION
========================================================= */

function deleteApplication(key){

  if(!isAdmin)return;

  if(!confirm(
    "क्या आप यह application delete करना चाहते हैं?"
  ))return;

  db.ref("applications/"+key).remove();

}


/* =========================================================
   NEWS LISTENER
========================================================= */

db.ref("news").on("value",snapshot=>{

  newsData=
    snapshot.val() || {};

  renderNews();

});


/* =========================================================
   ADD NEWS
========================================================= */

function addNews(){

  if(!isAdmin)return;

  const title=
    document.getElementById("newsTitle")
    .value.trim();

  const details=
    document.getElementById("newsDetails")
    .value.trim();

  if(!title||!details){

    alert(
      "News title aur details dono bharein."
    );

    return;

  }

  db.ref("news").push({

    title:title,

    details:details,

    createdAt:
      firebase.database.ServerValue.TIMESTAMP

  });

  document.getElementById("newsTitle").value="";
  document.getElementById("newsDetails").value="";

  alert("✅ News successfully added.");

}


/* =========================================================
   RENDER NEWS
========================================================= */

function renderNews(){

  const box=
    document.getElementById("newsList");

  if(!box)return;

  let html="";

  Object
  .entries(newsData)
  .sort((a,b)=>
    (b[1].createdAt||0)-
    (a[1].createdAt||0)
  )
  .forEach(([key,item])=>{

    let dateText="";

    if(item.createdAt){

      dateText=
        new Date(item.createdAt)
        .toLocaleString("en-IN");

    }

    const details=
      String(item.details||"");

    html+=`

      <div class="card news">

        <h3>
          📰 ${escapeHTML(item.title||"")}
        </h3>

        ${
          dateText
          ?`
          <div class="newsDate">
            ${dateText}
          </div>
          `
          :""
        }

        <p>
          ${escapeHTML(details.slice(0,280))}
          ${details.length>280?"...":""}
        </p>

        <button
          class="main readBtn"
          onclick="readNews('${key}')">

          📖 Read Full News

        </button>

        ${
          isAdmin
          ?`
          <div class="actions">

            <button
              class="orange"
              onclick="editNews('${key}')">
              ✏️ Edit
            </button>

            <button
              class="red"
              onclick="deleteNews('${key}')">
              🗑️ Delete
            </button>

          </div>
          `
          :""
        }

      </div>

    `;

  });

  if(!html){

    html=`
      <div class="card">
        <h3>🙏 स्वागत है</h3>
        <p>
          अभी कोई news उपलब्ध नहीं है।
        </p>
      </div>
    `;

  }

  box.innerHTML=html;

}


/* =========================================================
   READ NEWS
========================================================= */

function readNews(key){

  const item=
    newsData[key];

  if(!item)return;

  document
    .getElementById("modalTitle")
    .innerText=
    item.title||"";

  document
    .getElementById("modalDetails")
    .innerText=
    item.details||"";

  document
    .getElementById("newsModal")
    .style.display="block";

}


function closeNews(){

  document
    .getElementById("newsModal")
    .style.display="none";

}


/* =========================================================
   EDIT NEWS
========================================================= */

function editNews(key){

  if(!isAdmin)return;

  const item=
    newsData[key];

  const title=
    prompt(
      "News Title:",
      item.title||""
    );

  if(title===null)return;

  const details=
    prompt(
      "News Details:",
      item.details||""
    );

  if(details===null)return;

  if(!title.trim()||!details.trim()){

    alert(
      "Title aur details blank nahi ho sakte."
    );

    return;

  }

  db.ref("news/"+key)
    .update({

      title:title.trim(),

      details:details.trim()

    });

}


/* =========================================================
   DELETE NEWS
========================================================= */

function deleteNews(key){

  if(!isAdmin)return;

  if(!confirm(
    "क्या आप यह news delete करना चाहते हैं?"
  ))return;

  db.ref("news/"+key).remove();

}


/* =========================================================
   DEFAULT GALLERY
========================================================= */

const defaultGallery={

  photo1:{
    title:"श्री राम मंदिर",
    url:
      "https://upload.wikimedia.org/wikipedia/commons/8/87/Lord_-ram_temple.jpg"
  },

  photo2:{
    title:"राम मंदिर",
    url:
      "https://upload.wikimedia.org/wikipedia/commons/9/9e/Ram_Mandir_Ayodhya.jpg"
  },

  photo3:{
    title:"श्री राम",
    url:
      "https://upload.wikimedia.org/wikipedia/commons/7/7c/Rama.jpg"
  },

  photo4:{
    title:"मंदिर दर्शन",
    url:
      "https://upload.wikimedia.org/wikipedia/commons/6/6e/Ram_Mandir%2C_Ayodhya.jpg"
  }

};


/* =========================================================
   GALLERY LISTENER
========================================================= */

db.ref("gallery").on("value",snapshot=>{

  galleryData=
    snapshot.val() || {};

  renderGallery();

});


/* =========================================================
   RENDER GALLERY
========================================================= */

function renderGallery(){

  const box=
    document.getElementById("galleryList");

  if(!box)return;

  const data=
    Object.keys(galleryData).length
    ? galleryData
    : defaultGallery;

  let html="";

  Object
  .entries(data)
  .reverse()
  .forEach(([key,item])=>{

    html+=`

      <div class="galleryItem">

        <img
          src="${safeURL(item.url)}"
          alt="${escapeHTML(item.title||"Gallery")}"
          loading="lazy"
          onerror="this.style.display='none'">

        <div class="galleryCaption">

          ${escapeHTML(item.title||"Gallery Photo")}

          ${
            isAdmin && galleryData[key]
            ?`
            <div style="margin-top:8px">

              <button
                class="main red"
                onclick="deleteGallery('${key}')">

                🗑️ Delete

              </button>

            </div>
            `
            :""
          }

        </div>

      </div>

    `;

  });

  box.innerHTML=html;

}


/* =========================================================
   ADD GALLERY
========================================================= */

function addGallery(){

  if(!isAdmin)return;

  const title=
    document
      .getElementById("galleryTitle")
      .value.trim();

  const url=
    document
      .getElementById("galleryUrl")
      .value.trim();

  const status=
    document
      .getElementById("galleryStatus");

  if(!url){

    status.innerText=
      "❌ Image URL डालें.";

    return;

  }

  if(!/^https?:\/\//i.test(url)){

    status.innerText=
      "❌ Valid image URL डालें.";

    return;

  }

  db.ref("gallery").push({

    title:
      title||"Gallery Photo",

    url:url,

    createdAt:
      firebase.database.ServerValue.TIMESTAMP

  });

  document
    .getElementById("galleryTitle")
    .value="";

  document
    .getElementById("galleryUrl")
    .value="";

  status.innerText=
    "✅ Photo successfully added.";

}


/* =========================================================
   DELETE GALLERY
========================================================= */

function deleteGallery(key){

  if(!isAdmin)return;

  if(!confirm(
    "क्या आप यह gallery photo delete करना चाहते हैं?"
  ))return;

  db.ref("gallery/"+key).remove();

}


/* =========================================================
   SECURITY HELPERS
========================================================= */

function safeURL(url){

  const value=
    String(url||"").trim();

  if(/^https?:\/\//i.test(value)){

    return value.replace(/"/g,"%22");

  }

  return "";

}


function escapeHTML(value){

  return String(value||"")
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");

}


/* =========================================================
   CLOSE MODAL WHEN CLICKING OUTSIDE
========================================================= */

window.addEventListener("click",function(e){

  const modal=
    document.getElementById("newsModal");

  if(e.target===modal){

    closeNews();

  }

});

</script>

</body>
</html>
