<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</title>

<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-database-compat.js"></script>

<style>
*{box-sizing:border-box}

html{scroll-behavior:smooth}

body{
  margin:0;
  font-family:Arial,Helvetica,sans-serif;
  background:#fff8ef;
  color:#222;
}

header{
  background:linear-gradient(135deg,#7b0000,#c03900,#ff9800);
  color:white;
  text-align:center;
  padding:28px 15px;
}

header h1{
  margin:0;
  font-size:26px;
}

header p{
  margin:7px 0 0;
}

nav{
  position:sticky;
  top:0;
  z-index:100;
  background:#650000;
  display:flex;
  justify-content:center;
  flex-wrap:wrap;
}

nav a{
  color:white;
  text-decoration:none;
  padding:12px 14px;
  font-size:14px;
  font-weight:bold;
}

nav a:hover{
  background:#900000;
}

.container{
  max-width:1100px;
  margin:auto;
  padding:15px;
}

.hero{
  text-align:center;
  background:white;
  margin-top:20px;
  padding:30px 18px;
  border-radius:16px;
  box-shadow:0 3px 14px #0002;
}

.hero h2{
  color:#a00000;
}

.card{
  background:white;
  margin:20px 0;
  padding:20px;
  border-radius:16px;
  box-shadow:0 3px 14px #0002;
}

h2,h3{
  color:#970000;
}

input,textarea,select{
  width:100%;
  padding:12px;
  margin:6px 0 14px;
  border:1px solid #ccc;
  border-radius:8px;
  font-size:15px;
}

textarea{
  min-height:100px;
  resize:vertical;
}

button{
  border:0;
  border-radius:8px;
  padding:11px 16px;
  margin:4px;
  background:#a00000;
  color:white;
  font-weight:bold;
  cursor:pointer;
}

button:hover{
  opacity:.88;
}

.green{background:#16803c}
.red{background:#c5221f}
.orange{background:#e87500}
.gray{background:#555}

.row{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:15px;
}

.news{
  border:1px solid #eee;
  background:#fffdf9;
  border-radius:12px;
  padding:15px;
  margin:12px 0;
}

.news h3{
  margin-top:0;
}

.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
  gap:15px;
}

.gallery-card{
  background:#fffdf9;
  border:1px solid #eee;
  border-radius:12px;
  padding:10px;
}

.gallery-card img{
  width:100%;
  height:190px;
  object-fit:cover;
  border-radius:9px;
  background:#eee;
}

.application{
  border:1px solid #ddd;
  border-radius:12px;
  padding:15px;
  margin:12px 0;
  background:#fffdf9;
}

.status{
  display:inline-block;
  padding:5px 9px;
  border-radius:20px;
  font-size:12px;
  font-weight:bold;
}

.pending{
  background:#fff0b3;
  color:#765700;
}

.accepted{
  background:#c9f7d5;
  color:#086b25;
}

.rejected{
  background:#ffd0d0;
  color:#900;
}

.admin-box{
  background:#fff6df;
  border:1px solid #efd18c;
  border-radius:12px;
  padding:15px;
}

.hidden{
  display:none!important;
}

.small{
  font-size:13px;
  color:#666;
}

.message{
  padding:10px;
  border-radius:8px;
  margin-top:8px;
}

.success{
  background:#dff5e5;
  color:#126b2e;
}

.error{
  background:#ffe1e1;
  color:#9b0000;
}

footer{
  background:#580000;
  color:white;
  text-align:center;
  padding:25px 15px;
  margin-top:30px;
}

.danger-note{
  font-size:12px;
  color:#8a0000;
}

@media(max-width:650px){
  header h1{
    font-size:21px;
  }

  nav a{
    font-size:12px;
    padding:10px 8px;
  }

  .row{
    grid-template-columns:1fr;
    gap:0;
  }
}
</style>
</head>

<body>

<header>
  <h1>🚩 श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h1>
  <p>Siswa Bazar</p>
  <p>जय श्री राम 🚩</p>
</header>

<nav>
  <a href="#home">Home</a>
  <a href="#news">News</a>
  <a href="#gallery">Gallery</a>
  <a href="#volunteer">Volunteer</a>
  <a href="#committee">Committee</a>
  <a href="#admin">Admin</a>
</nav>

<div class="container">

<!-- HOME -->

<section id="home" class="hero">
  <h2>🙏 आपका हार्दिक स्वागत है 🙏</h2>

  <p>
    श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति,
    Siswa Bazar की वेबसाइट पर आपका स्वागत है।
  </p>

  <p><b>सेवा • सहयोग • संस्कार • समाज</b></p>

  <p>🚩 जय श्री राम 🚩</p>
</section>


<!-- NEWS -->

<section id="news" class="card">

  <h2>📰 News & Updates</h2>

  <div id="newsList">
    <p>News loading...</p>
  </div>

</section>


<!-- GALLERY -->

<section id="gallery" class="card">

  <h2>🖼️ Gallery</h2>

  <p class="small">
    Gallery में फोटो दिखाने के लिए admin को public/direct image URL डालना होगा।
  </p>

  <div id="galleryList" class="gallery">
    <p>Gallery loading...</p>
  </div>

</section>


<!-- VOLUNTEER -->

<section id="volunteer" class="card">

  <h2>🙋 Volunteer Registration</h2>

  <p>
    सेवा समिति से जुड़ने के लिए नीचे अपना आवेदन भेजें।
  </p>

  <form id="volunteerForm">

    <label>पूरा नाम *</label>
    <input id="vName" required>

    <div class="row">

      <div>
        <label>Mobile Number *</label>
        <input
          id="vMobile"
          type="tel"
          maxlength="10"
          pattern="[0-9]{10}"
          placeholder="10 digit mobile"
          required>
      </div>

      <div>
        <label>उम्र *</label>
        <input
          id="vAge"
          type="number"
          min="10"
          max="100"
          required>
      </div>

    </div>

    <label>पता *</label>
    <textarea id="vAddress" required></textarea>

    <label>आप किस प्रकार सेवा करना चाहते हैं?</label>
    <input
      id="vContribution"
      placeholder="जैसे व्यवस्था, सजावट, प्रसाद, सुरक्षा">

    <label>PDF Application / Google Drive Link</label>
    <input
      id="vPdf"
      type="url"
      placeholder="https://drive.google.com/...">

    <p class="small">
      PDF को Google Drive पर upload करके उसका shareable link यहां डाल सकते हैं।
    </p>

    <label>अन्य जानकारी</label>
    <textarea id="vMessage"></textarea>

    <button type="submit">
      आवेदन भेजें
    </button>

  </form>

  <div id="volunteerMsg"></div>

</section>


<!-- COMMITTEE -->

<section id="committee" class="card">

  <h2>👥 Committee Member Application</h2>

  <form id="committeeForm">

    <label>पूरा नाम *</label>
    <input id="cName" required>

    <label>Mobile Number *</label>
    <input
      id="cMobile"
      type="tel"
      maxlength="10"
      pattern="[0-9]{10}"
      required>

    <label>उम्र *</label>
    <input
      id="cAge"
      type="number"
      min="10"
      max="100"
      required>

    <label>पता *</label>
    <textarea id="cAddress" required></textarea>

    <label>समिति में आपका योगदान</label>
    <textarea id="cMessage"></textarea>

    <button type="submit">
      Committee Application भेजें
    </button>

  </form>

  <div id="committeeMsg"></div>

</section>


<!-- ADMIN -->

<section id="admin" class="card">

  <h2>🔐 Admin Panel</h2>

  <div id="loginBox" class="admin-box">

    <label>Admin Password</label>

    <input
      id="adminPassword"
      type="password"
      placeholder="Admin Password">

    <button onclick="adminLogin()">
      Login
    </button>

    <p class="small">
      केवल अधिकृत समिति प्रशासन के लिए।
    </p>

  </div>


  <div id="adminPanel" class="hidden">

    <h3>📊 Admin Dashboard</h3>

    <button onclick="showAdmin('applications')">
      Applications
    </button>

    <button onclick="showAdmin('news')">
      Add News
    </button>

    <button onclick="showAdmin('gallery')">
      Add Gallery
    </button>

    <button class="gray" onclick="adminLogout()">
      Logout
    </button>


    <!-- APPLICATIONS -->

    <div id="adminApplications">

      <h3>📋 Applications</h3>

      <div class="row">

        <div>
          <label>Status Filter</label>

          <select id="statusFilter"
                  onchange="loadApplications()">

            <option value="all">All</option>
            <option value="pending">Pending</option>
            <option value="accepted">Accepted</option>
            <option value="rejected">Rejected</option>

          </select>
        </div>

        <div>
          <label>Search</label>

          <input
            id="applicationSearch"
            placeholder="Name / Mobile"
            oninput="loadApplications()">
        </div>

      </div>

      <div id="applicationsList">
        Loading...
      </div>

    </div>


    <!-- ADD NEWS -->

    <div id="adminNews" class="hidden">

      <h3>📰 Add News</h3>

      <label>News Title</label>

      <input
        id="newsTitle"
        maxlength="150"
        placeholder="News title">

      <label>News Details</label>

      <textarea
        id="newsDetails"
        maxlength="1000"
        placeholder="News details"></textarea>

      <button onclick="addNews()">
        Publish News
      </button>

    </div>


    <!-- ADD GALLERY -->

    <div id="adminGallery" class="hidden">

      <h3>🖼️ Add Gallery Photo</h3>

      <p class="small">
        Firebase Storage इस्तेमाल नहीं हो रहा है।
        इसलिए public image URL डालना होगा।
      </p>

      <label>Photo Title</label>

      <input
        id="galleryTitle"
        placeholder="Photo title">

      <label>Image URL</label>

      <input
        id="galleryUrl"
        type="url"
        placeholder="https://example.com/photo.jpg">

      <button onclick="addGallery()">
        Add Photo
      </button>

    </div>

  </div>

</section>

</div>


<footer>

  <p>
    <b>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</b>
  </p>

  <p>Siswa Bazar</p>

  <p>🚩 जय श्री राम 🚩</p>

</footer>


<script>

/* =========================
   FIREBASE CONFIG
========================= */

const firebaseConfig = {
  apiKey: "AIzaSyDLonsbRwdlq3Ru4NIvhFqLzjKEUaPnzfc",
  authDomain: "shree-ram-janki-mandir-durga.firebaseapp.com",
  databaseURL: "https://shree-ram-janki-mandir-durga-default-rtdb.asia-southeast1.firebasedatabase.app",
  projectId: "shree-ram-janki-mandir-durga",
  storageBucket: "shree-ram-janki-mandir-durga.firebasestorage.app",
  messagingSenderId: "603852207772",
  appId: "1:603852207772:web:a27f2828d95284a4c69f59",
  measurementId: "G-9QQJJEMH1V"
};

firebase.initializeApp(firebaseConfig);

const db = firebase.database();


/* =========================
   ADMIN PASSWORD
========================= */

const ADMIN_PASSWORD = "SRJM2026";

let adminLoggedIn = false;


/* =========================
   HELPERS
========================= */

function escapeHTML(value){

  if(value === null || value === undefined){
    return "";
  }

  return String(value)
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");
}


function showMessage(id,text,type){

  const el = document.getElementById(id);

  el.className = "message " + type;

  el.textContent = text;
}


/* =========================
   VOLUNTEER SUBMIT
========================= */

document.getElementById("volunteerForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const name =
    document.getElementById("vName").value.trim();

  const mobile =
    document.getElementById("vMobile").value.trim();

  const age =
    document.getElementById("vAge").value.trim();

  const address =
    document.getElementById("vAddress").value.trim();

  const contribution =
    document.getElementById("vContribution").value.trim();

  const pdf =
    document.getElementById("vPdf").value.trim();

  const message =
    document.getElementById("vMessage").value.trim();


  if(!/^[0-9]{10}$/.test(mobile)){

    showMessage(
      "volunteerMsg",
      "कृपया सही 10 digit mobile number डालें।",
      "error"
    );

    return;
  }


  const data = {

    type:"Volunteer",

    name:name,

    mobile:mobile,

    age:age,

    address:address,

    contribution:contribution,

    pdfLink:pdf,

    message:message,

    status:"pending",

    createdAt:Date.now()

  };


  try{

    await db.ref("applications")
      .push(data);

    showMessage(
      "volunteerMsg",
      "✅ आपका Volunteer आवेदन सफलतापूर्वक भेज दिया गया है।",
      "success"
    );

    document.getElementById("volunteerForm").reset();

  }catch(error){

    console.error(error);

    showMessage(
      "volunteerMsg",
      "❌ आवेदन भेजने में समस्या हुई। Firebase Database Rules जांचें।",
      "error"
    );

  }

});


/* =========================
   COMMITTEE SUBMIT
========================= */

document.getElementById("committeeForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const name =
    document.getElementById("cName").value.trim();

  const mobile =
    document.getElementById("cMobile").value.trim();

  const age =
    document.getElementById("cAge").value.trim();

  const address =
    document.getElementById("cAddress").value.trim();

  const message =
    document.getElementById("cMessage").value.trim();


  if(!/^[0-9]{10}$/.test(mobile)){

    showMessage(
      "committeeMsg",
      "कृपया सही 10 digit mobile number डालें।",
      "error"
    );

    return;
  }


  const data = {

    type:"Committee",

    name:name,

    mobile:mobile,

    age:age,

    address:address,

    message:message,

    status:"pending",

    createdAt:Date.now()

  };


  try{

    await db.ref("applications")
      .push(data);

    showMessage(
      "committeeMsg",
      "✅ आपका Committee application सफलतापूर्वक भेज दिया गया है।",
      "success"
    );

    document.getElementById("committeeForm").reset();

  }catch(error){

    console.error(error);

    showMessage(
      "committeeMsg",
      "❌ Application submit नहीं हुआ। Firebase Database Rules जांचें।",
      "error"
    );

  }

});


/* =========================
   LOAD NEWS
========================= */

function loadNews(){

  db.ref("news")
    .on("value",function(snapshot){

      const list =
        document.getElementById("newsList");

      list.innerHTML="";

      if(!snapshot.exists()){

        list.innerHTML =
          "<p>अभी कोई news उपलब्ध नहीं है।</p>";

        return;
      }


      const arr=[];

      snapshot.forEach(function(child){

        arr.push({
          id:child.key,
          ...child.val()
        });

      });


      arr.sort((a,b)=>
        (b.createdAt||0)-(a.createdAt||0)
      );


      arr.forEach(function(item){

        const div =
          document.createElement("div");

        div.className="news";

        const date =
          item.createdAt
          ? new Date(item.createdAt)
              .toLocaleString("hi-IN")
          : "";

        div.innerHTML = `

          <h3>${escapeHTML(item.title)}</h3>

          <p>
            ${escapeHTML(item.details)}
          </p>

          <small>${escapeHTML(date)}</small>

        `;

        list.appendChild(div);

      });

    });

}


/* =========================
   ADD NEWS
========================= */

async function addNews(){

  if(!adminLoggedIn){

    alert("Admin login required.");

    return;
  }


  const title =
    document.getElementById("newsTitle")
      .value.trim();

  const details =
    document.getElementById("newsDetails")
      .value.trim();


  if(!title || !details){

    alert("Title और Details दोनों भरें।");

    return;
  }


  try{

    await db.ref("news").push({

      title:title,

      details:details,

      createdAt:Date.now()

    });


    document.getElementById("newsTitle")
      .value="";

    document.getElementById("newsDetails")
      .value="";

    alert("✅ News published.");

  }catch(error){

    console.error(error);

    alert("News publish नहीं हुई।");

  }

}


/* =========================
   LOAD GALLERY
========================= */

function loadGallery(){

  db.ref("gallery")
    .on("value",function(snapshot){

      const list =
        document.getElementById("galleryList");

      list.innerHTML="";


      if(!snapshot.exists()){

        list.innerHTML =
          "<p>अभी gallery खाली है।</p>";

        return;
      }


      const arr=[];


      snapshot.forEach(function(child){

        arr.push({
          id:child.key,
          ...child.val()
        });

      });


      arr.sort((a,b)=>
        (b.createdAt||0)-(a.createdAt||0)
      );


      arr.forEach(function(item){

        const div =
          document.createElement("div");

        div.className="gallery-card";


        const img =
          document.createElement("img");

        img.src=item.url;

        img.alt=item.title||"Gallery";

        img.loading="lazy";

        img.onerror=function(){

          img.style.display="none";

        };


        div.appendChild(img);


        const p =
          document.createElement("p");

        p.innerHTML =
          "<b>"+escapeHTML(item.title||"Gallery Photo")+"</b>";

        div.appendChild(p);


        list.appendChild(div);

      });

    });

}


/* =========================
   ADD GALLERY
========================= */

async function addGallery(){

  if(!adminLoggedIn){

    alert("Admin login required.");

    return;
  }


  const title =
    document.getElementById("galleryTitle")
      .value.trim();

  const url =
    document.getElementById("galleryUrl")
      .value.trim();


  if(!title || !url){

    alert("Photo title और URL दोनों भरें।");

    return;
  }


  try{

    await db.ref("gallery").push({

      title:title,

      url:url,

      createdAt:Date.now()

    });


    document.getElementById("galleryTitle")
      .value="";

    document.getElementById("galleryUrl")
      .value="";


    alert("✅ Gallery photo added.");

  }catch(error){

    console.error(error);

    alert("Gallery photo add नहीं हुई।");

  }

}


/* =========================
   ADMIN LOGIN
========================= */

function adminLogin(){

  const password =
    document.getElementById("adminPassword")
      .value;


  if(password === ADMIN_PASSWORD){

    adminLoggedIn=true;

    document.getElementById("loginBox")
      .classList.add("hidden");

    document.getElementById("adminPanel")
      .classList.remove("hidden");

    loadApplications();

  }else{

    alert("❌ गलत Admin Password");

  }

}


/* =========================
   ADMIN LOGOUT
========================= */

function adminLogout(){

  adminLoggedIn=false;

  document.getElementById("adminPanel")
    .classList.add("hidden");

  document.getElementById("loginBox")
    .classList.remove("hidden");

  document.getElementById("adminPassword")
    .value="";

}


/* =========================
   ADMIN SECTION
========================= */

function showAdmin(section){

  document.getElementById("adminApplications")
    .classList.add("hidden");

  document.getElementById("adminNews")
    .classList.add("hidden");

  document.getElementById("adminGallery")
    .classList.add("hidden");


  if(section==="applications"){

    document.getElementById("adminApplications")
      .classList.remove("hidden");

    loadApplications();

  }


  if(section==="news"){

    document.getElementById("adminNews")
      .classList.remove("hidden");

  }


  if(section==="gallery"){

    document.getElementById("adminGallery")
      .classList.remove("hidden");

  }

}


/* =========================
   LOAD APPLICATIONS
========================= */

let allApplications=[];


function loadApplications(){

  if(!adminLoggedIn){

    return;
  }


  db.ref("applications")
    .on("value",function(snapshot){

      allApplications=[];


      snapshot.forEach(function(child){

        allApplications.push({

          id:child.key,

          ...child.val()

        });

      });


      allApplications.sort((a,b)=>
        (b.createdAt||0)-(a.createdAt||0)
      );


      renderApplications();

    });

}


/* =========================
   RENDER APPLICATIONS
========================= */

function renderApplications(){

  const list =
    document.getElementById("applicationsList");

  const filter =
    document.getElementById("statusFilter")
      .value;

  const search =
    document.getElementById("applicationSearch")
      .value
      .trim()
      .toLo
