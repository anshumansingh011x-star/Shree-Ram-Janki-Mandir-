<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Shree Ram Janki Mandir Durga Puja Seva Samiti</title>

<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-database-compat.js"></script>

<style>
*{box-sizing:border-box}
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
  padding:25px 15px;
}
header h1{margin:0;font-size:25px}
header p{margin:8px 0 0}
.container{max-width:1000px;margin:auto;padding:18px}
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
.primary{background:#e65100;color:white}
.green{background:#16803c;color:white}
.red{background:#c62828;color:white}
.dark{background:#333;color:white}
input,textarea,select{
  width:100%;
  padding:12px;
  margin:7px 0 14px;
  border:1px solid #ccc;
  border-radius:8px;
  font-size:15px;
}
textarea{min-height:100px}
.hidden{display:none}
.center{text-align:center}
.nav{
  display:flex;
  flex-wrap:wrap;
  gap:8px;
  justify-content:center;
  padding:12px;
  background:white;
  position:sticky;
  top:0;
  z-index:10;
}
.nav button{background:#8b0000;color:white}
.status{
  display:inline-block;
  padding:5px 10px;
  border-radius:20px;
  font-size:12px;
  font-weight:bold;
}
.pending{background:#fff3cd;color:#856404}
.accepted{background:#d4edda;color:#155724}
.rejected{background:#f8d7da;color:#721c24}
.item{
  border:1px solid #ddd;
  border-radius:10px;
  padding:15px;
  margin:10px 0;
}
.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
  gap:10px;
}
.gallery img{
  width:100%;
  height:160px;
  object-fit:cover;
  border-radius:10px;
}
footer{
  background:#222;
  color:white;
  text-align:center;
  padding:20px;
  margin-top:30px;
}
</style>
</head>

<body>

<header>
<h1>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h1>
<p>Siswa Bazar</p>
</header>

<div class="nav">
<button onclick="showPage('home')">Home</button>
<button onclick="showPage('join')">Join Us</button>
<button onclick="showPage('news')">News</button>
<button onclick="showPage('gallery')">Gallery</button>
<button onclick="showPage('admin')">Admin</button>
</div>

<div class="container">

<!-- HOME -->
<section id="home">
<div class="card center">
<h2>जय श्री राम 🚩</h2>
<p>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति में आपका स्वागत है।</p>
<button class="primary" onclick="showPage('join')">Join Committee / Volunteer</button>
</div>

<div class="card">
<h2>हमसे जुड़ें</h2>
<p>आप Volunteer या Committee Member के रूप में अपना विवरण भेज सकते हैं।</p>
</div>

<div class="card">
<h2>Latest News</h2>
<div id="homeNews">Loading...</div>
</div>
</section>

<!-- JOIN -->
<section id="join" class="hidden">

<div class="card" id="joinChoice">
<h2 class="center">आप किस रूप में जुड़ना चाहते हैं?</h2>
<div class="center">
<button class="primary" onclick="openForm('volunteer')">🙋 Volunteer</button>
<button class="green" onclick="openForm('committee')">👥 Committee Member</button>
</div>
</div>

<div class="card hidden" id="joinForm">
<h2 id="formTitle"></h2>

<form onsubmit="submitApplication(event)">

<input type="hidden" id="memberType">

<label>पूरा नाम *</label>
<input id="name" required>

<label>मोबाइल नंबर *</label>
<input id="phone" type="tel" required>

<label>पता *</label>
<textarea id="address" required></textarea>

<label>उम्र</label>
<input id="age" type="number">

<label>आप क्या योगदान देना चाहते हैं?</label>
<textarea id="contribution"></textarea>

<label>अन्य जानकारी</label>
<textarea id="message"></textarea>

<button class="primary" type="submit">Submit Application</button>
<button type="button" onclick="backToChoice()">Back</button>

</form>
</div>

<div id="submitMessage"></div>
</section>

<!-- NEWS -->
<section id="news" class="hidden">
<div class="card">
<h2>Latest News</h2>
<div id="newsList">Loading...</div>
</div>
</section>

<!-- GALLERY -->
<section id="gallery" class="hidden">
<div class="card">
<h2>Gallery</h2>
<div class="gallery" id="galleryList">Loading...</div>
</div>
</section>

<!-- ADMIN -->
<section id="admin" class="hidden">

<div class="card" id="adminLogin">
<h2>🔐 Admin Login</h2>

<input type="password" id="adminPassword" placeholder="Admin Password">

<button class="primary" onclick="adminLogin()">Login</button>

<p id="loginMsg"></p>
</div>

<div id="adminPanel" class="hidden">

<div class="card">
<h2>Admin Panel</h2>
<p>Welcome Admin 👑</p>
<button class="red" onclick="adminLogout()">Logout</button>
</div>

<div class="card">
<h2>Applications</h2>

<select id="filterStatus" onchange="loadApplications()">
<option value="all">All</option>
<option value="pending">Pending</option>
<option value="accepted">Accepted</option>
<option value="rejected">Rejected</option>
</select>

<div id="applications">Loading...</div>
</div>

<div class="card">
<h2>📰 Add News</h2>

<input id="newsTitle" placeholder="News Title">

<textarea id="newsText" placeholder="News Details"></textarea>

<button class="primary" onclick="addNews()">Add News</button>

<div id="adminNews"></div>
</div>

<div class="card">
<h2>🖼️ Add Gallery Photo</h2>

<input id="photoTitle" placeholder="Photo Title">

<input id="photoUrl" placeholder="Image URL">

<button class="primary" onclick="addPhoto()">Add Photo</button>

<div id="adminGallery"></div>
</div>

</div>
</section>

</div>

<footer>
<p>© 2026 Shree Ram Janki Mandir Durga Puja Seva Samiti</p>
<p>जय श्री राम 🚩</p>
</footer>

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

firebase.initializeApp(firebaseConfig);

const db = firebase.database();


/* =========================================================
   ADMIN PASSWORD
   ========================================================= */

const ADMIN_PASSWORD = "123456";


/* =========================================================
   PAGE SYSTEM
   ========================================================= */

function showPage(page){

  document.querySelectorAll("section").forEach(x=>{
    x.classList.add("hidden");
  });

  document.getElementById(page).classList.remove("hidden");

  if(page==="news") loadNews();
  if(page==="gallery") loadGallery();
  if(page==="home") loadHomeNews();

  if(page==="admin" && sessionStorage.getItem("admin")==="yes"){
    document.getElementById("adminLogin").classList.add("hidden");
    document.getElementById("adminPanel").classList.remove("hidden");
    loadApplications();
    loadAdminNews();
    loadAdminGallery();
  }

  window.scrollTo(0,0);
}


/* =========================================================
   JOIN FORM
   ========================================================= */

function openForm(type){

  document.getElementById("joinChoice").classList.add("hidden");
  document.getElementById("joinForm").classList.remove("hidden");

  document.getElementById("memberType").value=type;

  if(type==="volunteer"){
    document.getElementById("formTitle").innerText="🙋 Volunteer Registration";
  }else{
    document.getElementById("formTitle").innerText="👥 Committee Member Registration";
  }
}

function backToChoice(){

  document.getElementById("joinForm").classList.add("hidden");
  document.getElementById("joinChoice").classList.remove("hidden");

}

function submitApplication(e){

  e.preventDefault();

  const type=document.getElementById("memberType").value;

  const data={

    type:type,

    name:document.getElementById("name").value.trim(),

    phone:document.getElementById("phone").value.trim(),

    address:document.getElementById("address").value.trim(),

    age:document.getElementById("age").value,

    contribution:document.getElementById("contribution").value.trim(),

    message:document.getElementById("message").value.trim(),

    status:"pending",

    createdAt:Date.now()

  };

  db.ref("applications").push(data)

  .then(()=>{

    document.getElementById("submitMessage").innerHTML=
    `<div class="card">
      <h3>✅ Application Submitted</h3>
      <p>Aapka application successfully submit ho gaya hai.</p>
      <p>Admin verification ke baad status update karega.</p>
    </div>`;

    document.querySelector("#joinForm form").reset();

  })

  .catch(error=>{

    alert("Submit Error: "+error.message);

  });

}


/* =========================================================
   ADMIN LOGIN
   ========================================================= */

function adminLogin(){

  const password=document.getElementById("adminPassword").value;

  if(password===ADMIN_PASSWORD){

    sessionStorage.setItem("admin","yes");

    document.getElementById("adminLogin").classList.add("hidden");

    document.getElementById("adminPanel").classList.remove("hidden");

    loadApplications();
    loadAdminNews();
    loadAdminGallery();

  }else{

    document.getElementById("loginMsg").innerText=
    "❌ Wrong password";

  }

}

function adminLogout(){

  sessionStorage.removeItem("admin");

  document.getElementById("adminPanel").classList.add("hidden");

  document.getElementById("adminLogin").classList.remove("hidden");

}


/* =========================================================
   APPLICATIONS
   ========================================================= */

function loadApplications(){

  const filter=document.getElementById("filterStatus").value;

  db.ref("applications").on("value",snapshot=>{

    const box=document.getElementById("applications");

    box.innerHTML="";

    if(!snapshot.exists()){

      box.innerHTML="<p>No applications found.</p>";

      return;

    }

    let found=false;

    snapshot.forEach(child=>{

      const d=child.val();

      if(filter!=="all" && d.status!==filter) return;

      found=true;

      const date=d.createdAt
      ? new Date(d.createdAt).toLocaleString("en-IN")
      : "";

      box.innerHTML+=`

      <div class="item">

        <h3>${escapeHtml(d.name)}</h3>

        <p>
        <b>Type:</b>
        ${d.type==="volunteer"?"Volunteer":"Committee Member"}
        </p>

        <p><b>Phone:</b> ${escapeHtml(d.phone)}</p>

        <p><b>Address:</b> ${escapeHtml(d.address)}</p>

        <p><b>Age:</b> ${escapeHtml(d.age||"-")}</p>

        <p><b>Contribution:</b>
        ${escapeHtml(d.contribution||"-")}</p>

        <p><b>Message:</b>
        ${escapeHtml(d.message||"-")}</p>

        <p><b>Submitted:</b> ${date}</p>

        <p>
        <span class="status ${d.status}">
        ${d.status.toUpperCase()}
        </span>
        </p>

        <button class="green"
        onclick="updateApplication('${child.key}','accepted')">
        ✅ Accept
        </button>

        <button class="red"
        onclick="updateApplication('${child.key}','rejected')">
        ❌ Reject
        </button>

        <button class="dark"
        onclick="deleteApplication('${child.key}')">
        🗑️ Delete
        </button>

      </div>

      `;

    });

    if(!found){
      box.innerHTML="<p>No applications in this category.</p>";
    }

  });

}


function updateApplication(id,status){

  db.ref("applications/"+id).update({
    status:status,
    updatedAt:Date.now()
  })
  .then(()=>{
    alert(
      status==="accepted"
      ? "Application Accepted ✅"
      : "Application Rejected ❌"
    );
  })
  .catch(err=>alert(err.message));

}


function deleteApplication(id){

  if(!confirm("Delete this application?")) return;

  db.ref("applications/"+id).remove();

}


/* =========================================================
   NEWS
   ========================================================= */

function addNews(){

  const title=document.getElementById("newsTitle").value.trim();
  const text=document.getElementById("newsText").value.trim();

  if(!title || !text){

    alert("Title aur details dono bhariye.");

    return;

  }

  db.ref("news").push({

    title:title,
    text:text,
    createdAt:Date.now()

  })
  .then(()=>{

    document.getElementById("newsTitle").value="";
    document.getElementById("newsText").value="";

    alert("News added ✅");

  });

}


function loadNews(){

  db.ref("news").orderByChild("createdAt").on("value",snapshot=>{

    const box=document.getElementById("newsList");

    box.innerHTML="";

    let arr=[];

    snapshot.forEach(child=>{

      arr.push({
        id:child.key,
        ...child.val()
      });

    });

    arr.reverse();

    if(arr.length===0){

      box.innerHTML="<p>No news available.</p>";

      return;

    }

    arr.forEach(n=>{

      box.innerHTML+=`

      <div class="item">

        <h3>${escapeHtml(n.title)}</h3>

        <p>${escapeHtml(n.text)}</p>

      </div>

      `;

    });

  });

}


function loadHomeNews(){

  db.ref("news").orderByChild("createdAt").limitToLast(3)
  .once("value",snapshot=>{

    const box=document.getElementById("homeNews");

    box.innerHTML="";

    let arr=[];

    snapshot.forEach(c=>{
      arr.push(c.val());
    });

    arr.reverse();

    if(!arr.length){

      box.innerHTML="<p>No news yet.</p>";

      return;

    }

    arr.forEach(n=>{

      box.innerHTML+=`

      <div class="item">

      <h3>${escapeHtml(n.title)}</h3>

      <p>${escapeHtml(n.text)}</p>

      </div>

      `;

    });

  });

}


function loadAdminNews(){

  db.ref("news").on("value",snapshot=>{

    const box=document.getElementById("adminNews");

    box.innerHTML="<hr>";

    snapshot.forEach(child=>{

      const n=child.val();

      box.innerHTML+=`

      <div class="item">

      <b>${escapeHtml(n.title)}</b>

      <p>${escapeHtml(n.text)}</p>

      <button class="red"
      onclick="deleteNews('${child.key}')">
      Delete
      </button>

      </div>

      `;

    });

  });

}


function deleteNews(id){

  if(confirm("Delete this news?")){

    db.ref("news/"+id).remove();

  }

}


/* =========================================================
   GALLERY
   ========================================================= */

function addPhoto(){

  const title=document.getElementById("photoTitle").value.trim();
  const url=document.getElementById("photoUrl").value.trim();

  if(!title || !url){

    alert("Title aur Image URL dijiye.");

    return;

  }

  db.ref("gallery").push({

    title:title,
    url:url,
    createdAt:Date.now()

  })
  .then(()=>{

    document.getElementById("photoTitle").value="";
    document.getElementById("photoUrl").value="";

    alert("Photo added ✅");

  });

}


function loadGallery(){

  db.ref("gallery").on("value",snapshot=>{

    const box=document.getElementById("galleryList");

    box.innerHTML="";

    snapshot.forEach(child=>{

      const p=child.val();

      box.innerHTML+=`

      <div>

      <img src="${escapeAttribute(p.url)}"
      alt="${escapeAttribute(p.title)}"
      onerror="this.style.display='none'">

      <p class="center">${escapeHtml(p.title)}</p>

      </div>

      `;

    });

    if(!snapshot.exists()){

      box.innerHTML="<p>No photos available.</p>";

    }

  });

}


function loadAdminGallery(){

  db.ref("gallery").on("value",snapshot=>{

    const box=document.getElementById("adminGallery");

    box.innerHTML="<hr>";

    snapshot.forEach(child=>{

      const p=child.val();

      box.innerHTML+=`

      <div class="item">

      <b>${escapeHtml(p.title)}</b>

      <br>

      <button class="red"
      onclick="deletePhoto('${child.key}')">
      Delete
      </button>

      </div>

      `;

    });

  });

}


function deletePhoto(id){

  if(confirm("Delete photo?")){

    db.ref("gallery/"+id).remove();

  }

}


/* =========================================================
   SECURITY / DISPLAY HELPERS
   ========================================================= */

function escapeHtml(value){

  return String(value ?? "")
  .replace(/&/g,"&amp;")
  .replace(/</g,"&lt;")
  .replace(/>/g,"&gt;")
  .replace(/"/g,"&quot;")
  .replace(/'/g,"&#039;");

}

function escapeAttribute(value){

  return String(value ?? "")
  .replace(/"/g,"&quot;")
  .replace(/'/g,"&#039;");

}


/* =========================================================
   START
   ========================================================= */

showPage("home");

</script>

</body>
</html>
