<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Shree Ram Janki Mandir Durga Puja Seva Samiti</title>

<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-database-compat.js"></script>

<style>
*{box-sizing:border-box}
body{
  margin:0;
  font-family:Arial,sans-serif;
  background:#fff8ed;
  color:#3d2100;
}
header{
  background:linear-gradient(135deg,#8b1e00,#e85d04,#ffb703);
  color:white;
  text-align:center;
  padding:25px 15px;
}
header h1{margin:0;font-size:25px}
header p{margin:8px 0 0;font-size:17px}

nav{
  position:sticky;
  top:0;
  z-index:10;
  background:#5b1600;
  display:flex;
  overflow-x:auto;
}
nav button{
  flex:1;
  min-width:110px;
  padding:14px 8px;
  border:0;
  background:none;
  color:white;
  font-weight:bold;
  cursor:pointer;
}

.container{
  max-width:1000px;
  margin:auto;
  padding:20px 14px;
}

.page{display:none}
.page.active{display:block}

.card{
  background:white;
  border-radius:16px;
  padding:18px;
  margin:15px 0;
  box-shadow:0 4px 15px #0002;
}

h2{
  color:#a52a00;
  border-bottom:2px solid #ffb703;
  padding-bottom:8px;
}

input,textarea,select{
  width:100%;
  padding:12px;
  margin:7px 0 12px;
  border:1px solid #ccc;
  border-radius:9px;
  font-size:15px;
}

textarea{min-height:100px;resize:vertical}

button.action{
  border:0;
  padding:12px 18px;
  border-radius:9px;
  background:#e85d04;
  color:white;
  font-weight:bold;
  cursor:pointer;
  margin:4px;
}

button.green{background:#198754}
button.red{background:#c1121f}
button.dark{background:#5b1600}

.status{
  display:inline-block;
  padding:5px 10px;
  border-radius:20px;
  font-size:12px;
  font-weight:bold;
}
.pending{background:#fff3cd;color:#856404}
.accepted{background:#d1e7dd;color:#0f5132}
.rejected{background:#f8d7da;color:#842029}

.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
  gap:12px;
}
.gallery img{
  width:100%;
  height:170px;
  object-fit:cover;
  border-radius:12px;
}

.adminBox{
  background:#fff3cd;
  border:1px solid #ffc107;
  padding:15px;
  border-radius:12px;
}

.application{
  border:1px solid #ddd;
  border-radius:12px;
  padding:15px;
  margin:12px 0;
  background:#fffdf8;
}

.application p{margin:7px 0}

.small{
  font-size:13px;
  color:#666;
}

footer{
  background:#5b1600;
  color:white;
  text-align:center;
  padding:20px;
  margin-top:30px;
}

#loading{
  text-align:center;
  padding:20px;
  font-weight:bold;
}
</style>
</head>

<body>

<header>
  <h1>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h1>
  <p>Shree Ram Janki Mandir Durga Puja Seva Samiti</p>
  <p>📍 Siswa Bazar</p>
  <h3>जय श्री राम 🚩</h3>
</header>

<nav>
  <button onclick="showPage('home')">🏠 Home</button>
  <button onclick="showPage('news')">📰 News</button>
  <button onclick="showPage('gallery')">🖼️ Gallery</button>
  <button onclick="showPage('volunteer')">🙋 Volunteer</button>
  <button onclick="showPage('committee')">👥 Committee</button>
  <button onclick="showPage('admin')">🔐 Admin</button>
</nav>

<div class="container">

<!-- HOME -->
<section id="home" class="page active">

<div class="card">
<h2>🙏 स्वागत है</h2>
<p>
श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति में आपका हार्दिक स्वागत है।
धार्मिक एवं सामाजिक सेवा कार्यों में सहभागिता के लिए हमारे साथ जुड़ें।
</p>
</div>

<div class="card">
<h2>🚩 हमारा उद्देश्य</h2>
<p>
समाज में धार्मिक, सामाजिक एवं सेवा कार्यों को बढ़ावा देना तथा
सभी सदस्यों और स्वयंसेवकों के सहयोग से कार्यक्रमों को सफल बनाना।
</p>
</div>

</section>


<!-- NEWS -->
<section id="news" class="page">

<div class="card">
<h2>📰 Latest News</h2>
<div id="newsList">
<div id="loading">News loading...</div>
</div>
</div>

</section>


<!-- GALLERY -->
<section id="gallery" class="page">

<div class="card">
<h2>🖼️ Gallery</h2>

<div id="galleryList" class="gallery">
<div>Gallery loading...</div>
</div>

</div>

</section>


<!-- VOLUNTEER -->
<section id="volunteer" class="page">

<div class="card">
<h2>🙋 Volunteer Registration</h2>

<p class="small">
नीचे अपनी जानकारी भरें। PDF document optional है।
PDF की अधिकतम size 500 KB रखी गई है।
</p>

<input id="vName" placeholder="पूरा नाम">
<input id="vMobile" maxlength="10" placeholder="10 अंकों का मोबाइल नंबर">
<input id="vAddress" placeholder="पूरा पता">
<input id="vAge" type="number" placeholder="उम्र">

<select id="vContribution">
<option value="">योगदान चुनें</option>
<option>धार्मिक सेवा</option>
<option>कार्यक्रम व्यवस्था</option>
<option>सफाई व्यवस्था</option>
<option>प्रसाद व्यवस्था</option>
<option>सुरक्षा व्यवस्था</option>
<option>अन्य</option>
</select>

<textarea id="vMessage" placeholder="अन्य जानकारी / संदेश"></textarea>

<label><b>📄 PDF Document</b></label>
<input id="vPdf" type="file" accept="application/pdf">

<button class="action" onclick="submitVolunteer()">
Submit Volunteer Application
</button>

<p id="volunteerMsg"></p>

</div>

</section>


<!-- COMMITTEE -->
<section id="committee" class="page">

<div class="card">

<h2>👥 Committee Member Application</h2>

<input id="cName" placeholder="पूरा नाम">
<input id="cMobile" maxlength="10" placeholder="10 अंकों का मोबाइल नंबर">
<input id="cAddress" placeholder="पूरा पता">
<input id="cAge" type="number" placeholder="उम्र">

<textarea id="cContribution"
placeholder="आप समिति में किस प्रकार योगदान देना चाहते हैं?"></textarea>

<textarea id="cMessage"
placeholder="अन्य जानकारी / संदेश"></textarea>

<label><b>📄 PDF Document (Optional)</b></label>
<input id="cPdf" type="file" accept="application/pdf">

<button class="action" onclick="submitCommittee()">
Submit Committee Application
</button>

<p id="committeeMsg"></p>

</div>

</section>


<!-- ADMIN -->
<section id="admin" class="page">

<div class="card" id="adminLogin">

<h2>🔐 Admin Login</h2>

<input id="adminPassword" type="password" placeholder="Admin Password">

<button class="action dark" onclick="adminLogin()">
Login
</button>

<p id="loginMsg"></p>

</div>


<div id="adminPanel" style="display:none">

<div class="card">
<h2>⚙️ Admin Dashboard</h2>

<button class="action dark" onclick="loadApplications()">
🔄 Refresh Applications
</button>

<button class="action" onclick="showAdminSection('volunteersAdmin')">
🙋 Volunteers
</button>

<button class="action" onclick="showAdminSection('committeeAdmin')">
👥 Committee
</button>

<button class="action" onclick="showAdminSection('newsAdmin')">
📰 News
</button>

<button class="action" onclick="showAdminSection('galleryAdmin')">
🖼️ Gallery
</button>

<button class="action red" onclick="adminLogout()">
Logout
</button>

</div>


<!-- VOLUNTEER ADMIN -->
<div class="card" id="volunteersAdmin">

<h2>🙋 Volunteer Applications</h2>

<select id="volunteerFilter" onchange="loadApplications()">
<option value="all">All</option>
<option value="pending">Pending</option>
<option value="accepted">Accepted</option>
<option value="rejected">Rejected</option>
</select>

<input id="volunteerSearch"
oninput="loadApplications()"
placeholder="नाम या मोबाइल से Search">

<div id="volunteerApplications"></div>

</div>


<!-- COMMITTEE ADMIN -->
<div class="card" id="committeeAdmin" style="display:none">

<h2>👥 Committee Applications</h2>

<select id="committeeFilter" onchange="loadApplications()">
<option value="all">All</option>
<option value="pending">Pending</option>
<option value="accepted">Accepted</option>
<option value="rejected">Rejected</option>
</select>

<input id="committeeSearch"
oninput="loadApplications()"
placeholder="नाम या मोबाइल से Search">

<div id="committeeApplications"></div>

</div>


<!-- NEWS ADMIN -->
<div class="card" id="newsAdmin" style="display:none">

<h2>📰 Add News</h2>

<input id="newsTitle" maxlength="150" placeholder="News Title">

<textarea id="newsDetails"
maxlength="1000"
placeholder="News Details"></textarea>

<button class="action" onclick="addNews()">
➕ Add News
</button>

<div id="adminNewsList"></div>

</div>


<!-- GALLERY ADMIN -->
<div class="card" id="galleryAdmin" style="display:none">

<h2>🖼️ Add Gallery Photo</h2>

<p class="small">
Image 300 KB से छोटी रखें क्योंकि photo Realtime Database में save होगी।
</p>

<input id="galleryTitle" placeholder="Photo Title">

<input id="galleryPhoto" type="file" accept="image/*">

<button class="action" onclick="addGalleryPhoto()">
📤 Upload Photo
</button>

<p id="galleryMsg"></p>

<div id="adminGalleryList"></div>

</div>

</div>

</section>

</div>

<footer>
जय श्री राम 🚩 | Shree Ram Janki Mandir Durga Puja Seva Samiti
</footer>


<script>

/* =====================================================
   FIREBASE CONFIG
   ===================================================== */

const firebaseConfig = {

  apiKey: "YAHAN_APNI_API_KEY_PASTE_KARO",

  authDomain:
  "shree-ram-janki-mandir-durga.firebaseapp.com",

  databaseURL:
  "https://shree-ram-janki-mandir-durga-default-rtdb.asia-southeast1.firebasedatabase.app",

  projectId:
  "shree-ram-janki-mandir-durga",

  storageBucket:
  "shree-ram-janki-mandir-durga.firebasestorage.app",

  messagingSenderId:
  "YAHAN_APNA_MESSAGING_SENDER_ID",

  appId:
  "YAHAN_APNA_APP_ID"

};

firebase.initializeApp(firebaseConfig);

const db = firebase.database();


/* =====================================================
   ADMIN PASSWORD
   ===================================================== */

const ADMIN_PASSWORD = "SRJM2026";

let isAdmin = false;


/* =====================================================
   PAGE SYSTEM
   ===================================================== */

function showPage(page){

  document.querySelectorAll(".page")
  .forEach(p => p.classList.remove("active"));

  document.getElementById(page)
  .classList.add("active");

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


/* =====================================================
   ADMIN LOGIN
   ===================================================== */

function adminLogin(){

  const password =
  document.getElementById("adminPassword").value;

  if(password === ADMIN_PASSWORD){

    isAdmin = true;

    document.getElementById("adminLogin")
    .style.display="none";

    document.getElementById("adminPanel")
    .style.display="block";

    loadApplications();
    loadAdminNews();
    loadAdminGallery();

  }else{

    document.getElementById("loginMsg")
    .innerHTML =
    "❌ गलत Admin Password";

  }

}


function adminLogout(){

  isAdmin=false;

  document.getElementById("adminPanel")
  .style.display="none";

  document.getElementById("adminLogin")
  .style.display="block";

  document.getElementById("adminPassword").value="";

}


function showAdminSection(section){

  document.getElementById("volunteersAdmin")
  .style.display="none";

  document.getElementById("committeeAdmin")
  .style.display="none";

  document.getElementById("newsAdmin")
  .style.display="none";

  document.getElementById("galleryAdmin")
  .style.display="none";

  document.getElementById(section)
  .style.display="block";

}


/* =====================================================
   FILE TO BASE64
   ===================================================== */

function fileToBase64(file){

  return new Promise((resolve,reject)=>{

    const reader = new FileReader();

    reader.onload = () =>
    resolve(reader.result);

    reader.onerror = reject;

    reader.readAsDataURL(file);

  });

}


/* =====================================================
   VOLUNTEER SUBMIT
   ===================================================== */

async function submitVolunteer(){

  const name =
  document.getElementById("vName").value.trim();

  const mobile =
  document.getElementById("vMobile").value.trim();

  const address =
  document.getElementById("vAddress").value.trim();

  const age =
  document.getElementById("vAge").value.trim();

  const contribution =
  document.getElementById("vContribution").value;

  const message =
  document.getElementById("vMessage").value.trim();

  const pdf =
  document.getElementById("vPdf").files[0];

  const msg =
  document.getElementById("volunteerMsg");


  if(!name || !mobile || !address || !age){

    msg.innerHTML =
    "⚠️ कृपया सभी जरूरी जानकारी भरें।";

    return;

  }

  if(!/^[0-9]{10}$/.test(mobile)){

    msg.innerHTML =
    "⚠️ मोबाइल नंबर 10 अंकों का होना चाहिए।";

    return;

  }

  if(pdf && pdf.size > 500 * 1024){

    msg.innerHTML =
    "⚠️ PDF 500 KB से छोटी रखें।";

    return;

  }

  msg.innerHTML="⏳ Submit हो रहा है...";


  try{

    let pdfData="";

    if(pdf){

      pdfData =
      await fileToBase64(pdf);

    }

    const id =
    db.ref("volunteers").push().key;

    await db.ref("volunteers/"+id).set({

      id:id,

      name:name,

      mobile:mobile,

      address:address,

      age:age,

      contribution:contribution,

      message:message,

      pdf:pdfData,

      pdfName:pdf ? pdf.name : "",

      status:"pending",

      createdAt:Date.now()

    });


    msg.innerHTML =
    "✅ आपका Volunteer Application सफलतापूर्वक submit हो गया।";

    document.getElementById("vName").value="";
    document.getElementById("vMobile").value="";
    document.getElementById("vAddress").value="";
    document.getElementById("vAge").value="";
    document.getElementById("vContribution").value="";
    document.getElementById("vMessage").value="";
    document.getElementById("vPdf").value="";


  }catch(error){

    console.error(error);

    msg.innerHTML =
    "❌ Submit नहीं हुआ: "+error.message;

  }

}


/* =====================================================
   COMMITTEE SUBMIT
   ===================================================== */

async function submitCommittee(){

  const name =
  document.getElementById("cName").value.trim();

  const mobile =
  document.getElementById("cMobile").value.trim();

  const address =
  document.getElementById("cAddress").value.trim();

  const age =
  document.getElementById("cAge").value.trim();

  const contribution =
  document.getElementById("cContribution").value.trim();

  const message =
  document.getElementById("cMessage").value.trim();

  const pdf =
  document.getElementById("cPdf").files[0];

  const msg =
  document.getElementById("committeeMsg");


  if(!name || !mobile || !address || !age){

    msg.innerHTML =
    "⚠️ कृपया सभी जरूरी जानकारी भरें।";

    return;

  }

  if(!/^[0-9]{10}$/.test(mobile)){

    msg.innerHTML =
    "⚠️ मोबाइल नंबर 10 अंकों का होना चाहिए।";

    return;

  }

  if(pdf && pdf.size > 500 * 1024){

    msg.innerHTML =
    "⚠️ PDF 500 KB से छोटी रखें।";

    return;

  }

  msg.innerHTML="⏳ Submit हो रहा है...";


  try{

    let pdfData="";

    if(pdf){

      pdfData =
      await fileToBase64(pdf);

    }

    const id =
    db.ref("committee").push().key;

    await db.ref("committee/"+id).set({

      id:id,

      name:name,

      mobile:mobile,

      address:address,

      age:age,

      contribution:contribution,

      message:message,

      pdf:pdfData,

      pdfName:pdf ? pdf.name : "",

      status:"pending",

      createdAt:Date.now()

    });


    msg.innerHTML =
    "✅ Committee application successfully submit हो गया।";

    document.getElementById("cName").value="";
    document.getElementById("cMobile").value="";
    document.getElementById("cAddress").value="";
    document.getElementById("cAge").value="";
    document.getElementById("cContribution").value="";
    document.getElementById("cMessage").value="";
    document.getElementById("cPdf").value="";


  }catch(error){

    console.error(error);

    msg.innerHTML =
    "❌ Submit नहीं हुआ: "+error.message;

  }

}


/* =====================================================
   ADMIN APPLICATIONS
   ===================================================== */

function loadApplications(){

  if(!isAdmin) return;

  loadVolunteers();
  loadCommittee();

}


function loadVolunteers(){

  db.ref("volunteers").once("value")
  .then(snapshot=>{

    const data=[];

    snapshot.forEach(child=>{

      data.push(child.val());

    });

    const filter =
    document.getElementById("volunteerFilter").value;

    const search =
    document.getElementById("volunteerSearch").value
    .toLowerCase();

    const list =
    document.getElementById("volunteerApplications");

    list.innerHTML="";

    data.reverse().forEach(v=>{

      if(filter!=="all" && v.status!==filter)
        return;

      if(search &&
        !v.name.toLowerCase().includes(search) &&
        !v.mobile.includes(search))
        return;


      const div =
      document.createElement("div");

      div.className="application";

      div.innerHTML=`

        <h3>🙋 ${escapeHTML(v.name)}</h3>

        <p><b>📱 Mobile:</b>
        ${escapeHTML(v.mobile)}</p>

        <p><b>🏠 Address:</b>
        ${escapeHTML(v.address)}</p>

        <p><b>🎂 Age:</b>
        ${escapeHTML(v.age)}</p>

        <p><b>🤝 Contribution:</b>
        ${escapeHTML(v.contribution || "-")}</p>

        <p><b>📝 Message:</b>
        ${escapeHTML(v.message || "-")}</p>

        <p>
        <b>Status:</b>
        <span class="status ${v.status}">
        ${v.status.toUpperCase()}
        </span>
        </p>

        ${
          v.pdf
          ?
          `<p>
          <button class="action"
          onclick="viewPDF('${v.id}','volunteers')">
          📄 View PDF
          </button>
          </p>`
          :
          `<p class="small">📄 No PDF submitted</p>`
        }

        ${
          v.status==="pending"
          ?
          `
          <button class="action green"
          onclick="updateStatus('volunteers','${v.id}','accepted')">
          ✅ Accept
          </button>

          <button class="action red"
          onclick="updateStatus('volunteers','${v.id}','rejected')">
          ❌ Reject
          </button>
          `
          :
          ""
        }

      `;

      list.appendChild(div);

    });

  });

}


/* =====================================================
   COMMITTEE ADMIN
   ===================================================== */

function loadCommittee(){

  db.ref("committee").once("value")
  .then(snapshot=>{

    const data=[];

    snapshot.forEach(child=>{

      data.push(child.val());

    });

    const filter =
    document.getElementById("committeeFilter").value;

    const search =
    document.getElementById("committeeSearch").value
    .toLowerCase();

    const list =
    document.getElementById("committeeApplications");

    list.innerHTML="";

    data.reverse().forEach(v=>{

      if(filter!=="all" && v.status!==filter)
        return;

      if(search &&
        !v.name.toLowerCase().includes(search) &&
        !v.mobile.includes(search))
        return;


      const div =
      document.createElement("div");

      div.className="application";

      div.innerHTML=`

        <h3>👥 ${escapeHTML(v.name)}</h3>

        <p><b>📱 Mobile:</b>
        ${escapeHTML(v.mobile)}</p>

        <p><b>🏠 Address:</b>
        ${escapeHTML(v.address)}</p>

        <p><b>🎂 Age:</b>
        ${escapeHTML(v.age)}</p>

        <p><b>🤝 Contribution:</b>
        ${escapeHTML(v.contribution || "-")}</p>

        <p><b>📝 Message:</b>
        ${escapeHTML(v.message || "-")}</p>

        <p>
        <b>Status:</b>
        <span class="status ${v.status}">
        ${v.status.toUpperCase()}
        </span>
        </p>

        ${
          v.pdf
          ?
          `<button class="action"
          onclick="viewPDF('${v.id}','committee')">
          📄 View PDF
          </button>`
          :
          `<p class="small">📄 No PDF submitted</p>`
        }

        ${
          v.status==="pending"
          ?
          `
          <button class="action green"
          onclick="updateStatus('committee','${v.id}','accepted')">
          ✅ Accept
          </button>

          <button class="action red"
          onclick="updateStatus('committee','${v.id}','rejected')">
          ❌ Reject
          </button>
          `
          :
          ""
        }

      `;

      list.appendChild(div);

    });

  });

}


/* =====================================================
   ACCEPT / REJECT
   ===================================================== */

function updateStatus(type,id,status){

  if(!isAdmin) return;

  db.ref(type+"/"+id+"/status")
  .set(status)
  .then(()=>{

    loadApplications();

  })
  .catch(error=>{

    alert(error.message);

  });

}


/* =====================================================
   VIEW PDF
   ===================================================== */

function viewPDF(id,type){

  db.ref(type+"/"+id+"/pdf")
  .once("value")
  .then(snapshot=>{

    const pdf =
    snapshot.val();

    if(!pdf){

      alert("PDF उपलब्ध नहीं है।");
      return;

    }

    const win =
    window.open();

    win.document.write(`

      <html>
      <head>
      <title>PDF</title>
      </head>

      <body style="margin:0">

      <iframe
      src="${pdf}"
      style="width:100%;height:100vh;border:0">
      </iframe>

      </body>
      </html>

    `);

  });

}


/* =====================================================
   NEWS
   ===================================================== */

function addNews(){

  if(!isAdmin) return;

  const title =
  document.getElementById("newsTitle").value.trim();

  const details =
  document.getElementById("newsDetails").value.trim();

  if(!title || !details){

    alert("Title और Details भरें।");
    return;

  }

  const id =
  db.ref("news").push().key;

  db.ref("news/"+id).set({

    id:id,

    title:title,

    details:details,

    createdAt:Date.now()

  })
  .then(()=>{

    document.getElementById("newsTitle").value="";
    document.getElementById("newsDetails").value="";

    loadNews();
    loadAdminNews();

    alert("✅ News added");

  });

}


function loadNews(){

  db.ref("news").once("value")
  .then(snapshot=>{

    const list =
    document.getElementById("newsList");

    list.innerHTML="";

    const data=[];

    snapshot.forEach(child=>{

      data.push(child.val());

    });

    data.reverse();

    if(data.length===0){

      list.innerHTML=
      "<p>अभी कोई News उपलब्ध नहीं है।</p>";

      return;

    }

    data.forEach(n=>{

      const div =
      document.createElement("div");

      div.className="card";

      div.innerHTML=`

        <h3>📰 ${escapeHTML(n.title)}</h3>

        <p>${escapeHTML(n.details)}</p>

        <p class="small">
        ${new Date(n.createdAt).toLocaleString("hi-IN")}
        </p>

      `;

      list.appendChild(div);

    });

  });

}


function loadAdminNews(){

  if(!isAdmin) return;

  db.ref("news").once("value")
  .then(snapshot=>{

    const list =
    document.getElementById("adminNewsList");

    list.innerHTML="";

    snapshot.forEach(child=>{

      const n=child.val();

      const div=
      document.createElement("div");

      div.className="application";

      div.innerHTML=`

        <b>${escapeHTML(n.title)}</b>

        <p>${escapeHTML(n.details)}</p>

        <button class="action red"
        onclick="deleteNews('${n.id}')">
        🗑️ Delete
        </button>

      `;

      list.prepend(div);

    });

  });

}


function deleteNews(id){

  if(!isAdmin) return;

  if(!confirm("News delete करें?"))
    return;

  db.ref("news/"+id)
  .remove()
  .then(()=>{

    loadNews();
    loadAdminNews();

  });

}


/* =====================================================
   GALLERY
   ===================================================== */

async function addGalleryPhoto(){

  if(!isAdmin) return;

  const title =
  document.getElementById("galleryTitle").value.trim();

  const file =
  document.getElementById("galleryPhoto").files[0];

  const msg =
  document.getElementById("galleryMsg");


  if(!file){

    msg.innerHTML="⚠️ Photo select करें।";
    return;

  }

  if(file.size > 300 * 1024){

    msg.innerHTML=
    "⚠️ Photo 300 KB से छोटी रखें।";

    return;

  }

  msg.innerHTML="⏳ Upload हो रहा है...";


  try{

    const image =
    await fileToBase64(file);

    const id =
    db.ref("gallery").push().key;

    await db.ref("gallery/"+id).set({

      id:id,

      title:title,

      image:image,

      createdAt:Date.now()

    });


    document.getElementById("galleryTitle").value="";
    document.getElementById("galleryPhoto").value="";

    msg.innerHTML="✅ Photo uploaded";

    loadGallery();
    loadAdminGallery();


  }catch(error){

    msg.innerHTML=
    "❌ Error: "+error.message;

  }

}


function loadGallery(){

  db.ref("gallery").once("value")
  .then(snapshot=>{

    const list =
    document.getElementById("galleryList");

    list.innerHTML="";

    const data=[];

    snapshot.forEach(child=>{

      data.push(child.val());

    });

    data.reverse();

    if(data.length===0){

      list.innerHTML=
      "<p>अभी Gallery खाली है।</p>";

      return;

    }

    data.forEach(g=>{

      const div =
      document.createElement("div");

      div.innerHTML=`

        <img
        src="${g.image}"
        alt="${escapeHTML(g.title || 'Gallery Photo')}">

      `;

      list.appendChild(div);

    });

  });

}


function loadAdminGallery(){

  if(!isAdmin) return;

  db.ref("gallery").once("value")
  .then(snapshot=>{

    const list =
    document.getElementById("adminGalleryList");

    list.innerHTML="";

    snapshot.forEach(child=>{

      const g=child.val();

      const div=
      document.createElement("div");

      div.className="application";

      div.innerHTML=`

        <img
        src="${g.image}"
        style="width:120px;height:100px;object-fit:cover;border-radius:8px">

        <p>
        <b>${escapeHTML(g.title || "Gallery Photo")}</b>
        </p>

        <button class="action red"
        onclick="deleteGallery('${g.id}')">
        🗑️ Delete
        </button>

      `;

      list.appendChild(div);

    });

  });

}


function deleteGallery(id){

  if(!isAdmin) return;

  if(!confirm("Photo delete करें?"))
    return;

  db.ref("gallery/"+id)
  .remove()
  .then(()=>{

    loadGallery();
    loadAdminGallery();

  });

}


/* =====================================================
   SECURITY HELPER
   ===================================================== */

function escapeHTML(value){

  if(value===undefined || value===null)
    return "";

  return String(value)
  .replace(/&/g,"&amp;")
  .replace(/</g,"&lt;")
  .replace(/>/g,"&gt;")
  .replace(/"/g,"&quot;")
  .replace(/'/g,"&#039;");

}


/* =====================================================
   START
   ===================================================== */

loadNews();
loadGallery();

</script>

</body>
</html>
