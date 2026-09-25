<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Shree Ram Janki Mandir Durga Puja Seva Samiti</title>

<!-- Firebase -->
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-database-compat.js"></script>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
  font-family:Arial,sans-serif;
}

body{
  background:#fff8ef;
  color:#222;
}

header{
  background:linear-gradient(135deg,#8b0000,#d35400);
  color:white;
  padding:22px 15px;
  text-align:center;
}

header h1{
  font-size:25px;
  margin-bottom:7px;
}

header p{
  font-size:14px;
}

nav{
  background:#fff;
  padding:10px;
  display:flex;
  justify-content:center;
  gap:8px;
  flex-wrap:wrap;
  box-shadow:0 2px 8px #0002;
  position:sticky;
  top:0;
  z-index:10;
}

nav button{
  border:0;
  background:#8b0000;
  color:#fff;
  padding:9px 14px;
  border-radius:20px;
  cursor:pointer;
}

section{
  max-width:900px;
  margin:auto;
  padding:28px 15px;
}

.card{
  background:white;
  padding:20px;
  margin:15px 0;
  border-radius:15px;
  box-shadow:0 3px 12px #0002;
}

h2{
  color:#8b0000;
  margin-bottom:15px;
}

input,textarea,select{
  width:100%;
  padding:12px;
  margin:7px 0 12px;
  border:1px solid #ccc;
  border-radius:8px;
  font-size:15px;
}

textarea{
  min-height:90px;
  resize:vertical;
}

.btn{
  background:#8b0000;
  color:white;
  border:0;
  padding:11px 18px;
  border-radius:8px;
  cursor:pointer;
  font-size:15px;
}

.btn.green{
  background:#16803c;
}

.btn.red{
  background:#b00020;
}

.btn.orange{
  background:#d35400;
}

.hidden{
  display:none!important;
}

.news{
  border-left:5px solid #d35400;
  padding:12px;
  margin:10px 0;
  background:#fff7ee;
  border-radius:8px;
}

.application{
  border:1px solid #ddd;
  padding:15px;
  border-radius:10px;
  margin:12px 0;
  background:#fff;
}

.status{
  display:inline-block;
  padding:5px 10px;
  border-radius:15px;
  font-size:12px;
  background:#eee;
}

.status.pending{
  background:#fff0b3;
}

.status.accepted{
  background:#c9f7d5;
  color:#12652c;
}

.status.rejected{
  background:#ffd0d0;
  color:#8b0000;
}

footer{
  background:#222;
  color:white;
  text-align:center;
  padding:25px 15px;
  margin-top:30px;
}

.notice{
  padding:12px;
  margin:10px 0;
  border-radius:8px;
  background:#fff3cd;
  color:#664d03;
}

.success{
  background:#d1e7dd;
  color:#0f5132;
}

.error{
  background:#f8d7da;
  color:#842029;
}

.loading{
  text-align:center;
  padding:20px;
  color:#777;
}

.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
  gap:12px;
}

.gallery img{
  width:100%;
  height:150px;
  object-fit:cover;
  border-radius:10px;
}

.admin-top{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:10px;
  flex-wrap:wrap;
}
</style>
</head>

<body>

<header>
  <h1>🚩 श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h1>
  <p>Siswa Bazar</p>
  <p>सेवा • सहयोग • संस्कार • समाज</p>
</header>

<nav>
  <button onclick="showSection('home')">Home</button>
  <button onclick="showSection('volunteer')">Volunteer</button>
  <button onclick="showSection('member')">Committee</button>
  <button onclick="showSection('news')">News</button>
  <button onclick="showSection('gallery')">Gallery</button>
  <button onclick="showSection('admin')">Admin</button>
</nav>

<!-- HOME -->
<section id="home">
  <div class="card">
    <h2>🙏 स्वागत है</h2>
    <p>
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति की आधिकारिक वेबसाइट
      पर आपका हार्दिक स्वागत है।
    </p>
    <br>
    <p>
      आप समिति से जुड़ने के लिए Volunteer या Committee Member के रूप में
      आवेदन कर सकते हैं।
    </p>
  </div>

  <div class="card">
    <h2>📢 नवीनतम सूचना</h2>
    <div id="homeNews">
      <div class="loading">News loading...</div>
    </div>
  </div>
</section>

<!-- VOLUNTEER -->
<section id="volunteer" class="hidden">
  <div class="card">
    <h2>🙋 Volunteer Registration</h2>

    <div id="volunteerMsg"></div>

    <input id="vName" placeholder="पूरा नाम">
    <input id="vPhone" placeholder="मोबाइल नंबर" maxlength="10">
    <input id="vVillage" placeholder="गांव / शहर">
    <input id="vAge" type="number" placeholder="उम्र">
    <textarea id="vReason" placeholder="आप समिति से क्यों जुड़ना चाहते हैं?"></textarea>

    <button class="btn" onclick="submitVolunteer()">
      आवेदन भेजें
    </button>
  </div>
</section>

<!-- MEMBER -->
<section id="member" class="hidden">
  <div class="card">
    <h2>👥 Committee Member Registration</h2>

    <div id="memberMsg"></div>

    <input id="mName" placeholder="पूरा नाम">
    <input id="mPhone" placeholder="मोबाइल नंबर" maxlength="10">
    <input id="mVillage" placeholder="गांव / शहर">
    <input id="mAge" type="number" placeholder="उम्र">

    <select id="mRole">
      <option value="">भूमिका चुनें</option>
      <option>Committee Member</option>
      <option>Volunteer Coordinator</option>
      <option>Event Coordinator</option>
      <option>Social Media</option>
      <option>Other</option>
    </select>

    <textarea id="mAbout" placeholder="अपने बारे में"></textarea>

    <button class="btn" onclick="submitMember()">
      आवेदन भेजें
    </button>
  </div>
</section>

<!-- NEWS -->
<section id="news" class="hidden">
  <div class="card">
    <h2>📰 Latest News</h2>
    <div id="newsList">
      <div class="loading">News loading...</div>
    </div>
  </div>
</section>

<!-- GALLERY -->
<section id="gallery" class="hidden">
  <div class="card">
    <h2>📸 Gallery</h2>

    <div class="gallery" id="galleryList">
      <p>Gallery में अभी कोई फोटो नहीं है।</p>
    </div>
  </div>
</section>

<!-- ADMIN -->
<section id="admin" class="hidden">
  <div class="card" id="adminLogin">
    <h2>🔐 Admin Panel</h2>

    <div id="adminMsg"></div>

    <input
      id="adminPassword"
      type="password"
      placeholder="Admin Password"
    >

    <button class="btn" onclick="adminLoginCheck()">
      Login
    </button>
  </div>

  <div class="card hidden" id="adminPanel">

    <div class="admin-top">
      <h2>⚙️ Admin Dashboard</h2>
      <button class="btn red" onclick="adminLogout()">Logout</button>
    </div>

    <hr><br>

    <h2>🙋 Volunteer Applications</h2>
    <div id="volunteerApplications">
      <div class="loading">Loading...</div>
    </div>

    <hr><br>

    <h2>👥 Committee Applications</h2>
    <div id="memberApplications">
      <div class="loading">Loading...</div>
    </div>

    <hr><br>

    <h2>📰 Add News</h2>

    <input id="newsTitle" placeholder="News Title">
    <textarea id="newsText" placeholder="News Description"></textarea>

    <button class="btn orange" onclick="addNews()">
      Add News
    </button>

    <div id="adminNewsList"></div>

  </div>
</section>

<footer>
  <p>© 2026 Shree Ram Janki Mandir Durga Puja Seva Samiti</p>
  <p>सभी अधिकार सुरक्षित</p>
</footer>

<script>

/* =========================================================
   FIREBASE CONFIG
========================================================= */

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


/* =========================================================
   FIREBASE INITIALIZATION
========================================================= */

let db = null;
let firebaseReady = false;

try {

  if (!firebase.apps.length) {
    firebase.initializeApp(firebaseConfig);
  }

  db = firebase.database();
  firebaseReady = true;

  console.log("Firebase connected successfully");

} catch(error) {

  console.error("Firebase initialization error:", error);

  document.body.insertAdjacentHTML(
    "afterbegin",
    `<div class="notice error">
      Firebase connection error. Website का basic interface फिर भी काम करेगा।
    </div>`
  );
}


/* =========================================================
   SECTION SYSTEM
========================================================= */

function showSection(id){

  const sections = [
    "home",
    "volunteer",
    "member",
    "news",
    "gallery",
    "admin"
  ];

  sections.forEach(section => {

    const element = document.getElementById(section);

    if(element){
      element.classList.add("hidden");
    }

  });

  const selected = document.getElementById(id);

  if(selected){
    selected.classList.remove("hidden");
  }

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });
}


/* =========================================================
   HELPERS
========================================================= */

function message(id,text,type=""){

  const element = document.getElementById(id);

  if(!element) return;

  element.innerHTML =
    `<div class="notice ${type}">${text}</div>`;
}


function clean(value){

  return String(value || "")
    .replace(/[<>]/g,"")
    .trim();
}


function validPhone(phone){

  return /^[6-9][0-9]{9}$/.test(phone);
}


function requireFirebase(){

  if(!firebaseReady || !db){

    alert(
      "Firebase अभी connected नहीं है। Firebase configuration और Database Rules check करें।"
    );

    return false;
  }

  return true;
}


/* =========================================================
   VOLUNTEER SUBMIT
========================================================= */

async function submitVolunteer(){

  if(!requireFirebase()) return;

  const name = clean(document.getElementById("vName").value);
  const phone = clean(document.getElementById("vPhone").value);
  const village = clean(document.getElementById("vVillage").value);
  const age = clean(document.getElementById("vAge").value);
  const reason = clean(document.getElementById("vReason").value);

  if(!name || !phone){

    message(
      "volunteerMsg",
      "कृपया नाम और मोबाइल नंबर भरें।",
      "error"
    );

    return;
  }

  if(!validPhone(phone)){

    message(
      "volunteerMsg",
      "कृपया सही 10 digit मोबाइल नंबर डालें।",
      "error"
    );

    return;
  }

  try{

    const ref = db.ref("volunteers").push();

    await ref.set({

      name:name,
      phone:phone,
      village:village,
      age:age,
      reason:reason,

      status:"pending",

      createdAt:Date.now()

    });

    message(
      "volunteerMsg",
      "✅ आपका Volunteer आवेदन सफलतापूर्वक भेज दिया गया है। Admin verification के बाद status update होगा।",
      "success"
    );

    document.getElementById("vName").value="";
    document.getElementById("vPhone").value="";
    document.getElementById("vVillage").value="";
    document.getElementById("vAge").value="";
    document.getElementById("vReason").value="";

  }catch(error){

    console.error(error);

    message(
      "volunteerMsg",
      "आवेदन भेजने में समस्या हुई: " + error.message,
      "error"
    );
  }
}


/* =========================================================
   MEMBER SUBMIT
========================================================= */

async function submitMember(){

  if(!requireFirebase()) return;

  const name = clean(document.getElementById("mName").value);
  const phone = clean(document.getElementById("mPhone").value);
  const village = clean(document.getElementById("mVillage").value);
  const age = clean(document.getElementById("mAge").value);
  const role = clean(document.getElementById("mRole").value);
  const about = clean(document.getElementById("mAbout").value);

  if(!name || !phone){

    message(
      "memberMsg",
      "कृपया नाम और मोबाइल नंबर भरें।",
      "error"
    );

    return;
  }

  if(!validPhone(phone)){

    message(
      "memberMsg",
      "कृपया सही 10 digit मोबाइल नंबर डालें।",
      "error"
    );

    return;
  }

  try{

    const ref = db.ref("committeeMembers").push();

    await ref.set({

      name:name,
      phone:phone,
      village:village,
      age:age,
      role:role,
      about:about,

      status:"pending",

      createdAt:Date.now()

    });

    message(
      "memberMsg",
      "✅ आपका Committee Member आवेदन सफलतापूर्वक भेज दिया गया है।",
      "success"
    );

    document.getElementById("mName").value="";
    document.getElementById("mPhone").value="";
    document.getElementById("mVillage").value="";
    document.getElementById("mAge").value="";
    document.getElementById("mRole").value="";
    document.getElementById("mAbout").value="";

  }catch(error){

    console.error(error);

    message(
      "memberMsg",
      "आवेदन भेजने में समस्या हुई: " + error.message,
      "error"
    );
  }
}


/* =========================================================
   ADMIN LOGIN
========================================================= */

function adminLoginCheck(){

  const password =
    document.getElementById("adminPassword").value;

  /*
    Current admin password:
    SRJM2026
  */

  if(password === "SRJM2026"){

    localStorage.setItem("srjm_admin","true");

    document
      .getElementById("adminLogin")
      .classList.add("hidden");

    document
      .getElementById("adminPanel")
      .classList.remove("hidden");

    loadAdminData();

  }else{

    message(
      "adminMsg",
      "❌ गलत Admin Password",
      "error"
    );
  }
}


function adminLogout(){

  localStorage.removeItem("srjm_admin");

  document
    .getElementById("adminPanel")
    .classList.add("hidden");

  document
    .getElementById("adminLogin")
    .classList.remove("hidden");

  document.getElementById("adminPassword").value="";
}


/* =========================================================
   ADMIN APPLICATIONS
========================================================= */

function loadAdminData(){

  if(!requireFirebase()) return;

  loadVolunteers();
  loadMembers();
  loadAdminNews();
}


function loadVolunteers(){

  db.ref("volunteers").on("value",snapshot=>{

    const container =
      document.getElementById("volunteerApplications");

    if(!snapshot.exists()){

      container.innerHTML =
        "<p>अभी कोई Volunteer application नहीं है।";

      return;
    }

    let html="";

    snapshot.forEach(child=>{

      const data = child.val();
      const id = child.key;

      html += applicationHTML(
        id,
        data,
        "volunteer"
      );

    });

    container.innerHTML=html;

  });
}


function loadMembers(){

  db.ref("committeeMembers").on("value",snapshot=>{

    const container =
      document.getElementById("memberApplications");

    if(!snapshot.exists()){

      container.innerHTML =
        "<p>अभी कोई Committee application नहीं है।";

      return;
    }

    let html="";

    snapshot.forEach(child=>{

      const data=child.val();
      const id=child.key;

      html += applicationHTML(
        id,
        data,
        "member"
      );

    });

    container.innerHTML=html;

  });
}


function applicationHTML(id,data,type){

  const status =
    data.status || "pending";

  let extra="";

  if(type==="volunteer"){

    extra = `
      <p><b>उद्देश्य:</b> ${clean(data.reason)}</p>
    `;

  }else{

    extra = `
      <p><b>भूमिका:</b> ${clean(data.role)}</p>
      <p><b>About:</b> ${clean(data.about)}</p>
    `;
  }

  return `
    <div class="application">

      <p><b>नाम:</b> ${clean(data.name)}</p>

      <p><b>मोबाइल:</b> ${clean(data.phone)}</p>

      <p><b>गांव/शहर:</b> ${clean(data.village)}</p>

      <p><b>उम्र:</b> ${clean(data.age)}</p>

      ${extra}

      <p>
        <b>Status:</b>
        <span class="status ${status}">
          ${status.toUpperCase()}
        </span>
      </p>

      <br>

      <button
        class="btn green"
        onclick="updateApplication('${type}','${id}','accepted')"
      >
        ✓ Accept
      </button>

      <button
        class="btn red"
        onclick="updateApplication('${type}','${id}','rejected')"
      >
        ✕ Reject
      </button>

      <button
        class="btn"
        onclick="deleteApplication('${type}','${id}')"
      >
        Delete
      </button>

    </div>
  `;
}


/* =========================================================
   ACCEPT / REJECT
========================================================= */

async function updateApplication(type,id,status){

  if(!requireFirebase()) return;

  const path =
    type==="volunteer"
      ? "volunteers/"
      : "committeeMembers/";

  try{

    await db.ref(path + id).update({

      status:status,
      updatedAt:Date.now()

    });

    alert(
      status==="accepted"
        ? "Application Accepted ✅"
        : "Application Rejected ❌"
    );

  }catch(error){

    alert(
      "Status update failed: " +
      error.message
    );
  }
}


async function deleteApplication(type,id){

  if(!requireFirebase()) return;

  if(!confirm("क्या आप इस application को delete करना चाहते हैं?")){
    return;
  }

  const path =
    type==="volunteer"
      ? "volunteers/"
      : "committeeMembers/";

  try{

    await db.ref(path + id).remove();

  }catch(error){

    alert(
      "Delete failed: " +
      error.message
    );
  }
}


/* =========================================================
   NEWS
========================================================= */

async function addNews(){

  if(!requireFirebase()) return;

  const title =
    clean(document.getElementById("newsTitle").value);

  const text =
    clean(document.getElementById("newsText").value);

  if(!title || !text){

    alert("News title और description भरें।");

    return;
  }

  try{

    const ref = db.ref("news").push();

    await ref.set({

      title:title,
      text:text,
      createdAt:Date.now()

    });

    document.getElementById("newsTitle").value="";
    document.getElementById("newsText").value="";

    alert("News successfully added ✅");

  }catch(error){

    alert(
      "News add failed: " +
      error.message
    );
  }
}


function loadNews(){

  if(!firebaseReady || !db) return;

  db.ref("news")
    .orderByChild("createdAt")
    .on("value",snapshot=>{

      let html="";

      const items=[];

      snapshot.forEach(child=>{

        items.push({
          id:child.key,
          ...child.val()
        });

      });

      items.reverse();

      if(items.length===0){

        html="<p>अभी कोई news उपलब्ध नहीं है।";

      }else{

        items.forEach(item=>{

          html += `
            <div class="news">
              <h3>${clean(item.title)}</h3>
              <p>${clean(item.text)}</p>
            </div>
          `;

        });
      }

      const list =
        document.getElementById("newsList");

      const home =
        document.getElementById("homeNews");

      if(list) list.innerHTML=html;
      if(home) home.innerHTML=html;

    });
}


function loadAdminNews(){

  if(!firebaseReady || !db) return;

  db.ref("news")
    .orderByChild("createdAt")
    .on("value",snapshot=>{

      const container =
        document.getElementById("adminNewsList");

      if(!container) return;

      let html="";

      snapshot.forEach(child=>{

        const data=child.val();
        const id=child.key;

        html += `
          <div class="application">

            <h3>${clean(data.title)}</h3>

            <p>${clean(data.text)}</p>

            <br>

            <button
              class="btn red"
              onclick="deleteNews('${id}')"
            >
              Delete News
            </button>

          </div>
        `;

      });

      container.innerHTML =
        html || "<p>No news.</p>";

    });
}


async function deleteNews(id){

  if(!requireFirebase()) return;

  if(!confirm("News delete करें?")){
    return;
  }

  try{

    await db.ref("news/" + id).remove();

  }catch(error){

    alert(error.message);

  }
}


/* =========================================================
   STARTUP
========================================================= */

document.addEventListener("DOMContentLoaded",()=>{

  loadNews();

  if(localStorage.getItem("srjm_admin")==="true"){

    document
      .getElementById("adminLogin")
      .classList.add("hidden");

    document
      .getElementById("adminPanel")
      .classList.remove("hidden");

    loadAdminData();

  }

  console.log(
    "Shree Ram Janki Mandir website loaded."
  );

});

</script>

</body>
</html>
