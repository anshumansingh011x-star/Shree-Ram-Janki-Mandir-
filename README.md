<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>Shree Ram Janki Mandir Durga Puja Seva Samiti</title>

<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-database-compat.js"></script>

<style>
:root{
  --maroon:#68151c;
  --maroon2:#8e222b;
  --gold:#d5a646;
  --cream:#fffaf0;
  --light:#f7f2e8;
  --dark:#241b19;
  --muted:#756966;
  --white:#fff;
  --green:#218739;
  --red:#bd2525;
  --shadow:0 10px 30px rgba(70,30,20,.10);
}

*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

html{
  scroll-behavior:smooth;
}

body{
  font-family:Arial,Helvetica,sans-serif;
  background:var(--cream);
  color:var(--dark);
  line-height:1.6;
}

a{
  color:inherit;
  text-decoration:none;
}

button,input,textarea,select{
  font:inherit;
}

.container{
  width:min(1100px,92%);
  margin:auto;
}

/* HEADER */
header{
  background:linear-gradient(135deg,#551017,#7d1c25);
  color:white;
  border-bottom:3px solid var(--gold);
  position:sticky;
  top:0;
  z-index:1000;
  box-shadow:0 5px 20px rgba(0,0,0,.15);
}

.header-inner{
  min-height:78px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:20px;
}

.brand{
  display:flex;
  align-items:center;
  gap:12px;
}

.logo{
  width:48px;
  height:48px;
  border-radius:50%;
  background:linear-gradient(135deg,#f2d27b,#b8831d);
  color:#5b151b;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:24px;
  box-shadow:0 4px 12px rgba(0,0,0,.2);
}

.brand h1{
  font-size:18px;
  line-height:1.2;
}

.brand p{
  font-size:12px;
  opacity:.85;
  margin-top:3px;
}

nav{
  display:flex;
  gap:6px;
  flex-wrap:wrap;
  justify-content:flex-end;
}

nav a{
  padding:8px 11px;
  border-radius:8px;
  font-size:13px;
  transition:.2s;
}

nav a:hover{
  background:rgba(255,255,255,.13);
  color:#ffe29a;
}

/* HERO */
.hero{
  min-height:390px;
  display:flex;
  align-items:center;
  text-align:center;
  position:relative;
  overflow:hidden;
  background:
    radial-gradient(circle at 50% 20%,rgba(255,221,130,.18),transparent 32%),
    linear-gradient(135deg,#5c121a,#821f28 55%,#5b1218);
  color:white;
}

.hero:before{
  content:"";
  position:absolute;
  inset:18px;
  border:1px solid rgba(234,194,91,.35);
  border-radius:22px;
  pointer-events:none;
}

.hero-content{
  position:relative;
  z-index:2;
  width:100%;
  padding:45px 15px;
}

.om{
  font-size:42px;
  color:#f0ca66;
  margin-bottom:8px;
}

.hero h2{
  font-size:clamp(27px,5vw,48px);
  margin-bottom:8px;
}

.hero h3{
  font-size:clamp(17px,3vw,25px);
  color:#f5d37b;
  font-weight:600;
}

.hero p{
  max-width:700px;
  margin:15px auto 24px;
  opacity:.92;
}

.hero-btn{
  display:inline-block;
  background:linear-gradient(135deg,#e5bd5e,#b88626);
  color:#4e1318;
  font-weight:700;
  padding:11px 20px;
  border-radius:9px;
  box-shadow:0 5px 16px rgba(0,0,0,.2);
}

/* SECTIONS */
section{
  padding:55px 0;
}

section:nth-of-type(even){
  background:#fffdf7;
}

.section-title{
  text-align:center;
  margin-bottom:30px;
}

.section-title h2{
  color:var(--maroon);
  font-size:28px;
}

.section-title p{
  color:var(--muted);
  margin-top:5px;
  font-size:14px;
}

.gold-line{
  width:60px;
  height:3px;
  background:var(--gold);
  margin:10px auto;
  border-radius:10px;
}

/* WELCOME */
.welcome-box{
  background:white;
  border:1px solid #eadfca;
  border-radius:16px;
  padding:28px;
  text-align:center;
  box-shadow:var(--shadow);
}

.welcome-box h2{
  color:var(--maroon);
  margin-bottom:8px;
}

/* CARDS */
.cards{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:18px;
}

.card{
  background:white;
  border:1px solid #eadfca;
  border-radius:15px;
  padding:22px;
  text-align:center;
  box-shadow:var(--shadow);
  transition:.2s;
}

.card:hover{
  transform:translateY(-3px);
}

.card-icon{
  width:55px;
  height:55px;
  margin:0 auto 12px;
  border-radius:50%;
  background:#fff2d0;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:25px;
}

.card h3{
  color:var(--maroon);
  margin-bottom:7px;
}

.card p{
  color:var(--muted);
  font-size:14px;
}

/* NEWS */
.news-list{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:18px;
}

.news-card{
  background:white;
  border:1px solid #eadfca;
  border-left:4px solid var(--gold);
  border-radius:13px;
  padding:20px;
  box-shadow:var(--shadow);
}

.news-card h3{
  color:var(--maroon);
  margin-bottom:5px;
}

.news-date{
  font-size:12px;
  color:#8a746c;
  margin-bottom:10px;
}

.news-details{
  white-space:pre-wrap;
  color:#4c4140;
  font-size:14px;
}

.read-more{
  display:inline-block;
  margin-top:12px;
  color:var(--maroon2);
  font-weight:bold;
  font-size:13px;
}

/* FORMS */
.form-box{
  max-width:800px;
  margin:auto;
  background:white;
  padding:25px;
  border:1px solid #eadfca;
  border-radius:16px;
  box-shadow:var(--shadow);
}

.form-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:15px;
}

.field{
  display:flex;
  flex-direction:column;
  gap:6px;
}

.field.full{
  grid-column:1/-1;
}

label{
  font-size:13px;
  font-weight:700;
  color:#4b3935;
}

input,textarea,select{
  width:100%;
  border:1px solid #d9cdbb;
  border-radius:9px;
  padding:11px 12px;
  background:#fffdfa;
  outline:none;
}

input:focus,textarea:focus,select:focus{
  border-color:var(--gold);
  box-shadow:0 0 0 3px rgba(213,166,70,.12);
}

textarea{
  min-height:100px;
  resize:vertical;
}

.btn{
  border:0;
  border-radius:9px;
  padding:11px 17px;
  cursor:pointer;
  font-weight:700;
  transition:.2s;
}

.btn-primary{
  background:var(--maroon);
  color:white;
}

.btn-primary:hover{
  background:var(--maroon2);
}

.btn-gold{
  background:var(--gold);
  color:#4c171b;
}

.btn-green{
  background:var(--green);
  color:white;
}

.btn-red{
  background:var(--red);
  color:white;
}

.btn-gray{
  background:#eee7dc;
  color:#3f3431;
}

.submit-row{
  margin-top:18px;
  display:flex;
  justify-content:flex-end;
  gap:10px;
}

/* ADMIN */
.admin-login{
  max-width:430px;
  margin:auto;
  background:white;
  border:1px solid #eadfca;
  border-radius:16px;
  padding:25px;
  box-shadow:var(--shadow);
}

.admin-panel{
  margin-top:25px;
}

.admin-top{
  background:linear-gradient(135deg,#5d131a,#81232b);
  color:white;
  padding:20px;
  border-radius:15px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:15px;
  margin-bottom:20px;
}

.admin-top h3{
  color:#f5d37b;
}

.admin-help{
  font-size:13px;
  opacity:.85;
}

.admin-tools{
  display:flex;
  gap:10px;
  flex-wrap:wrap;
  margin-bottom:18px;
}

.admin-tools input,
.admin-tools select{
  max-width:250px;
}

.admin-list{
  display:grid;
  gap:14px;
}

.admin-item{
  background:white;
  border:1px solid #eadfca;
  border-radius:13px;
  padding:18px;
  box-shadow:var(--shadow);
}

.admin-item h4{
  color:var(--maroon);
  margin-bottom:5px;
}

.admin-meta{
  font-size:13px;
  color:#756966;
  margin-bottom:10px;
}

.status{
  display:inline-block;
  padding:4px 9px;
  border-radius:20px;
  font-size:11px;
  font-weight:bold;
  margin-bottom:10px;
}

.status-pending{
  background:#fff0bd;
  color:#7b5a00;
}

.status-accepted{
  background:#dff5e2;
  color:#17672a;
}

.status-rejected{
  background:#ffe0e0;
  color:#8c2020;
}

.admin-actions{
  display:flex;
  gap:7px;
  flex-wrap:wrap;
  margin-top:12px;
}

.news-admin{
  margin-top:30px;
  padding-top:25px;
  border-top:1px solid #eadfca;
}

.news-admin h3{
  color:var(--maroon);
  margin-bottom:15px;
}

/* TOAST */
#toast{
  position:fixed;
  right:18px;
  bottom:18px;
  background:#251b19;
  color:white;
  padding:12px 16px;
  border-radius:10px;
  box-shadow:0 8px 25px rgba(0,0,0,.25);
  opacity:0;
  transform:translateY(15px);
  pointer-events:none;
  transition:.25s;
  z-index:5000;
  max-width:330px;
  font-size:13px;
}

#toast.show{
  opacity:1;
  transform:translateY(0);
}

/* FOOTER */
footer{
  background:#421015;
  color:white;
  padding:30px 0;
  text-align:center;
  border-top:3px solid var(--gold);
}

footer h3{
  color:#f1ca68;
  margin-bottom:5px;
}

footer p{
  font-size:13px;
  opacity:.82;
}

/* MOBILE */
@media(max-width:800px){
  .header-inner{
    flex-direction:column;
    padding:12px 0;
  }

  nav{
    justify-content:center;
  }

  nav a{
    font-size:12px;
    padding:7px 8px;
  }

  .hero{
    min-height:360px;
  }

  .hero:before{
    inset:10px;
  }

  section{
    padding:42px 0;
  }

  .cards,
  .news-list{
    grid-template-columns:1fr;
  }

  .form-grid{
    grid-template-columns:1fr;
  }

  .field.full{
    grid-column:auto;
  }

  .admin-top{
    flex-direction:column;
    align-items:flex-start;
  }

  .admin-tools{
    flex-direction:column;
  }

  .admin-tools input,
  .admin-tools select{
    max-width:none;
  }
}
</style>
</head>

<body>

<!-- HEADER -->
<header>
  <div class="container header-inner">

    <a href="#home" class="brand">
      <div class="logo">🚩</div>
      <div>
        <h1>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h1>
        <p>Siswa Bazar</p>
      </div>
    </a>

    <nav>
      <a href="#home">Home</a>
      <a href="#news">Latest News</a>
      <a href="#volunteer">Volunteer</a>
      <a href="#committee">Committee</a>
      <a href="#admin">Admin Panel</a>
    </nav>

  </div>
</header>


<!-- HOME -->
<section id="home" class="hero">
  <div class="container hero-content">

    <div class="om">ॐ</div>

    <h2>जय श्री राम 🚩</h2>

    <h3>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h3>

    <p>
      सेवा, संस्कार और समाज के प्रति समर्पण के साथ
      मंदिर एवं धार्मिक आयोजनों में सहयोग करें।
    </p>

    <a href="#volunteer" class="hero-btn">
      Volunteer बनें
    </a>

  </div>
</section>


<!-- WELCOME -->
<section>
  <div class="container">

    <div class="welcome-box">
      <h2>आपका हार्दिक स्वागत है 🙏</h2>

      <div class="gold-line"></div>

      <p>
        श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति,
        Siswa Bazar की आधिकारिक वेबसाइट पर आपका स्वागत है।
        धार्मिक सेवा, मंदिर व्यवस्था एवं दुर्गा पूजा आयोजन में
        अपना सहयोग देने के लिए Volunteer या Committee Member के रूप में
        आवेदन कर सकते हैं।
      </p>
    </div>

  </div>
</section>


<!-- SERVICES -->
<section>
  <div class="container">

    <div class="section-title">
      <h2>हमारी सेवाएँ</h2>
      <div class="gold-line"></div>
      <p>मंदिर और धार्मिक आयोजनों में सहयोग के प्रमुख क्षेत्र</p>
    </div>

    <div class="cards">

      <div class="card">
        <div class="card-icon">🛕</div>
        <h3>Temple Service</h3>
        <p>
          मंदिर की व्यवस्था, साफ-सफाई और धार्मिक सेवा में सहयोग।
        </p>
      </div>

      <div class="card">
        <div class="card-icon">🤝</div>
        <h3>Volunteer</h3>
        <p>
          विभिन्न सेवा कार्यों के लिए Volunteer के रूप में आवेदन करें।
        </p>
      </div>

      <div class="card">
        <div class="card-icon">🙏</div>
        <h3>Durga Puja</h3>
        <p>
          दुर्गा पूजा एवं अन्य धार्मिक आयोजनों की व्यवस्था में सहयोग।
        </p>
      </div>

    </div>

  </div>
</section>


<!-- NEWS -->
<section id="news">
  <div class="container">

    <div class="section-title">
      <h2>Latest News</h2>
      <div class="gold-line"></div>
      <p>समिति की नवीनतम जानकारी और घोषणाएँ</p>
    </div>

    <div id="newsList" class="news-list">
      <div class="news-card">
        <h3>News Loading...</h3>
        <p>कृपया कुछ क्षण प्रतीक्षा करें।</p>
      </div>
    </div>

  </div>
</section>


<!-- VOLUNTEER -->
<section id="volunteer">
  <div class="container">

    <div class="section-title">
      <h2>Volunteer Application</h2>
      <div class="gold-line"></div>
      <p>समिति की सेवा के लिए अपना आवेदन भेजें</p>
    </div>

    <div class="form-box">

      <form id="volunteerForm">

        <div class="form-grid">

          <div class="field">
            <label>पूरा नाम *</label>
            <input id="vName" required>
          </div>

          <div class="field">
            <label>मोबाइल नंबर *</label>
            <input id="vMobile"
                   type="tel"
                   maxlength="10"
                   pattern="[0-9]{10}"
                   required>
          </div>

          <div class="field">
            <label>आयु *</label>
            <input id="vAge" type="number" min="1" max="100" required>
          </div>

          <div class="field">
            <label>सेवा का प्रकार *</label>
            <select id="vSupport" required>
              <option value="">Select Service</option>
              <option>पूजा / धार्मिक सेवा</option>
              <option>मंदिर व्यवस्था</option>
              <option>दुर्गा पूजा आयोजन</option>
              <option>साफ-सफाई / व्यवस्था</option>
              <option>प्रचार-प्रसार</option>
              <option>सोशल मीडिया / ऑनलाइन कार्य</option>
              <option>आर्थिक सहयोग</option>
              <option>भोजन / प्रसाद व्यवस्था</option>
              <option>सुरक्षा / भीड़ व्यवस्था</option>
              <option>अन्य सेवा</option>
            </select>
          </div>

          <div class="field full">
            <label>पूरा पता *</label>
            <textarea id="vAddress" required></textarea>
          </div>

          <div class="field full">
            <label>योगदान / अनुभव</label>
            <input id="vContribution"
                   placeholder="आप किस प्रकार सहयोग करना चाहते हैं?">
          </div>

          <div class="field">
            <label>Photo URL</label>
            <input id="vPhoto"
                   type="url"
                   placeholder="https://...">
          </div>

          <div class="field">
            <label>PDF Application Link</label>
            <input id="vPdf"
                   type="url"
                   placeholder="https://...">
          </div>

          <div class="field full">
            <label>अन्य जानकारी / संदेश</label>
            <textarea id="vMessage"></textarea>
          </div>

        </div>

        <div class="submit-row">
          <button class="btn btn-primary" type="submit">
            Volunteer Application भेजें
          </button>
        </div>

      </form>

    </div>

  </div>
</section>


<!-- COMMITTEE -->
<section id="committee">
  <div class="container">

    <div class="section-title">
      <h2>Committee Application</h2>
      <div class="gold-line"></div>
      <p>समिति से जुड़ने के लिए आवेदन करें</p>
    </div>

    <div class="form-box">

      <form id="committeeForm">

        <div class="form-grid">

          <div class="field">
            <label>पूरा नाम *</label>
            <input id="cName" required>
          </div>

          <div class="field">
            <label>मोबाइल नंबर *</label>
            <input id="cMobile"
                   type="tel"
                   maxlength="10"
                   pattern="[0-9]{10}"
                   required>
          </div>

          <div class="field">
            <label>आयु *</label>
            <input id="cAge" type="number" min="1" max="100" required>
          </div>

          <div class="field full">
            <label>पूरा पता *</label>
            <textarea id="cAddress" required></textarea>
          </div>

          <div class="field full">
            <label>योगदान / अनुभव</label>
            <textarea id="cContribution"></textarea>
          </div>

          <div class="field">
            <label>Photo URL</label>
            <input id="cPhoto"
                   type="url"
                   placeholder="https://...">
          </div>

          <div class="field full">
            <label>अन्य जानकारी / संदेश</label>
            <textarea id="cMessage"></textarea>
          </div>

        </div>

        <div class="submit-row">
          <button class="btn btn-primary" type="submit">
            Committee Application भेजें
          </button>
        </div>

      </form>

    </div>

  </div>
</section>


<!-- ADMIN -->
<section id="admin">
  <div class="container">

    <div class="section-title">
      <h2>Admin Panel</h2>
      <div class="gold-line"></div>
      <p>Applications और News manage करें</p>
    </div>

    <!-- LOGIN -->
    <div id="adminLoginBox" class="admin-login">

      <div class="field">
        <label>Admin Password</label>

        <input id="adminPassword"
               type="password"
               placeholder="Password">
      </div>

      <div class="submit-row">
        <button class="btn btn-primary"
                onclick="adminLogin()">
          Login
        </button>
      </div>

    </div>


    <!-- ADMIN PANEL -->
    <div id="adminPanel" class="admin-panel" style="display:none;">

      <div class="admin-top">

        <div>
          <h3>Admin Dashboard</h3>
          <div class="admin-help">
            Manage Applications • News
          </div>
        </div>

        <button class="btn btn-gold"
                onclick="adminLogout()">
          Logout
        </button>

      </div>


      <!-- APPLICATIONS -->
      <div>

        <div class="section-title" style="text-align:left;margin-bottom:15px;">
          <h2 style="font-size:23px;">Applications</h2>
          <p>Volunteer और Committee applications</p>
        </div>

        <div class="admin-tools">

          <input id="applicationSearch"
                 placeholder="Name / Mobile search..."
                 oninput="renderApplications()">

          <select id="applicationFilter"
                  onchange="renderApplications()">
            <option value="all">All</option>
            <option value="pending">Pending</option>
            <option value="accepted">Accepted</option>
            <option value="rejected">Rejected</option>
          </select>

        </div>

        <div id="applicationsList" class="admin-list"></div>

      </div>


      <!-- NEWS ADMIN -->
      <div class="news-admin">

        <h3>News Management</h3>

        <form id="newsForm">

          <input type="hidden" id="newsEditId">

          <div class="form-grid">

            <div class="field full">
              <label>News Title *</label>
              <input id="newsTitle"
                     maxlength="150"
                     required>
            </div>

            <div class="field full">
              <label>News Details *</label>
              <textarea id="newsDetails"
                        maxlength="1000"
                        required></textarea>
            </div>

          </div>

          <div class="submit-row">

            <button type="button"
                    class="btn btn-gray"
                    onclick="clearNewsForm()">
              Clear
            </button>

            <button type="submit"
                    class="btn btn-primary">
              <span id="newsSaveText">Add News</span>
            </button>

          </div>

        </form>

        <div id="adminNewsList"
             class="admin-list"
             style="margin-top:20px;">
        </div>

      </div>

    </div>

  </div>
</section>


<!-- FOOTER -->
<footer>
  <div class="container">

    <h3>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h3>

    <p>Siswa Bazar</p>

    <p style="margin-top:8px;">
      जय श्री राम 🚩 • सेवा ही समर्पण है
    </p>

    <p style="margin-top:12px;font-size:11px;">
      © 2026 Shree Ram Janki Mandir Durga Puja Seva Samiti
    </p>

  </div>
</footer>


<div id="toast"></div>


<script>

/* =========================
   FIREBASE CONFIG
========================= */

const firebaseConfig = {
  apiKey: "AIzaSyDLonsbRwdlq3Ru4NIvhfQqLzjKEUaPnzfc",
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
   HELPERS
========================= */

function toast(message){

  const el = document.getElementById("toast");

  el.textContent = message;

  el.classList.add("show");

  setTimeout(()=>{
    el.classList.remove("show");
  },3000);
}


function escapeHTML(value){

  return String(value ?? "")
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");
}


function safeURL(url){

  if(!url) return "";

  try{

    const u = new URL(url);

    if(u.protocol === "http:" ||
       u.protocol === "https:"){

      return u.href;
    }

  }catch(e){}

  return "";
}


function formatDate(value){

  if(!value) return "";

  const d = new Date(value);

  if(isNaN(d.getTime())) return "";

  return d.toLocaleString("en-IN",{
    dateStyle:"medium",
    timeStyle:"short"
  });
}


/* =========================
   NEWS - PUBLIC
========================= */

function loadNews(){

  db.ref("news").on("value",(snapshot)=>{

    const list = document.getElementById("newsList");

    list.innerHTML = "";

    const data = snapshot.val();

    if(!data){

      list.innerHTML = `
        <div class="news-card">
          <h3>अभी कोई News नहीं है</h3>
          <p>
            नई जानकारी जल्द ही यहाँ दिखाई जाएगी।
          </p>
        </div>
      `;

      return;
    }

    const news = Object.entries(data)
      .map(([id,item])=>({
        id,
        ...item
      }))
      .sort((a,b)=>
        Number(b.createdAt || 0) -
        Number(a.createdAt || 0)
      );

    news.forEach(item=>{

      const card = document.createElement("div");

      card.className = "news-card";

      card.innerHTML = `
        <h3>${escapeHTML(item.title)}</h3>

        <div class="news-date">
          ${escapeHTML(formatDate(item.createdAt))}
        </div>

        <div class="news-details">
          ${escapeHTML(item.details)}
        </div>

        <div class="read-more">
          Read More →
        </div>
      `;

      list.appendChild(card);

    });

  },(error)=>{

    document.getElementById("newsList").innerHTML = `
      <div class="news-card">
        <h3>News load नहीं हो पाई</h3>
        <p>Firebase connection/rules check करें।</p>
      </div>
    `;

    console.error(error);

  });

}


/* =========================
   VOLUNTEER FORM
========================= */

document.getElementById("volunteerForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const mobile =
    document.getElementById("vMobile").value.trim();

  if(!/^[0-9]{10}$/.test(mobile)){

    toast("सही 10 digit mobile number डालें।");

    return;
  }

  const data = {

    type:"volunteer",

    name:document.getElementById("vName").value.trim(),

    mobile:mobile,

    age:document.getElementById("vAge").value.trim(),

    address:document.getElementById("vAddress").value.trim(),

    support:document.getElementById("vSupport").value,

    contribution:
      document.getElementById("vContribution").value.trim(),

    photo:
      document.getElementById("vPhoto").value.trim(),

    pdf:
      document.getElementById("vPdf").value.trim(),

    message:
      document.getElementById("vMessage").value.trim(),

    status:"pending",

    createdAt:Date.now()

  };

  try{

    await db.ref("applications").push(data);

    this.reset();

    toast("Volunteer application successfully भेज दी गई।");

  }catch(error){

    console.error(error);

    toast("Application submit नहीं हुई। Firebase rules check करें।");

  }

});


/* =========================
   COMMITTEE FORM
========================= */

document.getElementById("committeeForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const mobile =
    document.getElementById("cMobile").value.trim();

  if(!/^[0-9]{10}$/.test(mobile)){

    toast("सही 10 digit mobile number डालें।");

    return;
  }

  const data = {

    type:"committee",

    name:document.getElementById("cName").value.trim(),

    mobile:mobile,

    age:document.getElementById("cAge").value.trim(),

    address:document.getElementById("cAddress").value.trim(),

    contribution:
      document.getElementById("cContribution").value.trim(),

    photo:
      document.getElementById("cPhoto").value.trim(),

    message:
      document.getElementById("cMessage").value.trim(),

    status:"pending",

    createdAt:Date.now()

  };

  try{

    await db.ref("applications").push(data);

    this.reset();

    toast("Committee application successfully भेज दी गई।");

  }catch(error){

    console.error(error);

    toast("Application submit नहीं हुई। Firebase rules check करें।");

  }

});


/* =========================
   ADMIN LOGIN
========================= */

function adminLogin(){

  const password =
    document.getElementById("adminPassword").value;

  if(password !== "SRJM2026"){

    toast("गलत Admin Password!");

    return;
  }

  sessionStorage.setItem("srjmAdmin","true");

  document.getElementById("adminLoginBox").style.display="none";

  document.getElementById("adminPanel").style.display="block";

  renderApplications();

  renderAdminNews();

  toast("Admin Panel खुल गया।");
}


function adminLogout(){

  sessionStorage.removeItem("srjmAdmin");

  document.getElementById("adminLoginBox").style.display="block";

  document.getElementById("adminPanel").style.display="none";

  document.getElementById("adminPassword").value="";

  toast("Admin logout हो गया।");
}


/* =========================
   APPLICATIONS
========================= */

let applicationsCache = {};


function renderApplications(){

  if(sessionStorage.getItem("srjmAdmin") !== "true") return;

  db.ref("applications").once("value")
  .then(snapshot=>{

    const data = snapshot.val() || {};

    applicationsCache = data;

    const search =
      document.getElementById("applicationSearch")
      .value
      .trim()
      .toLowerCase();

    const filter =
      document.getElementById("applicationFilter").value;

    const list =
      document.getElementById("applicationsList");

    list.innerHTML = "";

    let items = Object.entries(data)
      .map(([id,item])=>({
        id,
        ...item
      }))
      .sort((a,b)=>
        Number(b.createdAt || 0) -
        Number(a.createdAt || 0)
      );

    items = items.filter(item=>{

      const matchesSearch =
        !search ||
        String(item.name || "")
          .toLowerCase()
          .includes(search) ||
        String(item.mobile || "")
          .toLowerCase()
          .includes(search);

      const matchesFilter =
        filter === "all" ||
        item.status === filter;

      return matchesSearch && matchesFilter;

    });


    if(items.length === 0){

      list.innerHTML = `
        <div class="admin-item">
          कोई application नहीं मिली।
        </div>
      `;

      return;
    }


    items.forEach(item=>{

      const status =
        item.status || "pending";

      const statusClass =
        status === "accepted"
          ? "status-accepted"
          : status === "rejected"
          ? "status-rejected"
          : "status-pending";


      const photoURL =
        safeURL(item.photo);

      const pdfURL =
        safeURL(item.pdf);


      const div =
        document.createElement("div");

      div.className="admin-item";


      div.innerHTML = `

        <h4>
          ${escapeHTML(item.name)}
        </h4>

        <div class="admin-meta">
          Type:
          <b>${escapeHTML(
            item.type === "committee"
              ? "Committee"
              : "Volunteer"
          )}</b>
          <br>

          Mobile:
          <b>${escapeHTML(item.mobile)}</b>
          <br>

          Age:
          ${escapeHTML(item.age)}
          <br>

          Date:
          ${escapeHTML(formatDate(item.createdAt))}
        </div>

        <span class="status ${statusClass}">
          ${escapeHTML(status.toUpperCase())}
        </span>

        <p>
          <b>Address:</b><br>
          ${escapeHTML(item.address)}
        </p>

        ${
          item.support
          ? `
            <p style="margin-top:8px;">
              <b>Service:</b>
              ${escapeHTML(item.support)}
            </p>
          `
          : ""
        }

        ${
          item.contribution
          ? `
            <p style="margin-top:8px;">
              <b>Contribution / Experience:</b><br>
              ${escapeHTML(item.contribution)}
            </p>
          `
          : ""
        }

        ${
          item.message
          ? `
            <p style="margin-top:8px;">
              <b>Message:</b><br>
              ${escapeHTML(item.message)}
            </p>
          `
          : ""
        }

        ${
          photoURL
          ? `
            <p style="margin-top:8px;">
              <a href="${photoURL}"
                 target="_blank"
                 rel="noopener"
                 class="btn btn-gray"
                 style="display:inline-block;">
                 View Photo
              </a>
            </p>
          `
          : ""
        }

        ${
          pdfURL
          ? `
            <p style="margin-top:8px;">
              <a href="${pdfURL}"
                 target="_blank"
                 rel="noopener"
                 class="btn btn-gray"
                 style="display:inline-block;">
                 View PDF
              </a>
            </p>
          `
          : ""
        }

        <div class="admin-actions">

          <button
            class="btn btn-green"
            onclick="updateApplicationStatus('${item.id}','accepted')">
            Accept
          </button>

          <button
            class="btn btn-red"
            onclick="updateApplicationStatus('${item.id}','rejected')">
            Reject
          </button>

          <button
            class="btn btn-gray"
            onclick="deleteApplication('${item.id}')">
            Delete
          </button>

        </div>
      `;

      list.appendChild(div);

    });

  })
  .catch(error=>{

    console.error(error);

    toast("Applications load नहीं हुईं।");

  });

}


async function updateApplicationStatus(id,status){

  if(sessionStorage.getItem("srjmAdmin") !== "true")
    return;

  try{

    await db.ref("applications/"+id)
      .update({
        status:status,
        updatedAt:Date.now()
      });

    renderApplications();

    toast(
      status === "accepted"
      ? "Application Accept कर दी गई।"
      : "Application Reject कर दी गई।"
    );

  }catch(error){

    console.error(error);

    toast("Status update नहीं हुआ।");

  }

}


async function deleteApplication(id){

  if(sessionStorage.getItem("srjmAdmin") !== "true")
    return;

  if(!confirm("क्या आप इस application को delete करना चाहते हैं?"))
    return;

  try{

    await db.ref("applications/"+id).remove();

    renderApplications();

    toast("Application delete हो गई।");

  }catch(error){

    console.error(error);

    toast("Application delete नहीं हुई।");

  }

}


/* =========================
   ADMIN NEWS
========================= */

document.getElementById("newsForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  if(sessionStorage.getItem("srjmAdmin") !== "true"){
    toast("पहले Admin Login करें।");
    return;
  }


  const id =
    document.getElementById("newsEditId").value;

  const title =
    document.getElementById("newsTitle")
    .value
    .trim();

  const details =
    document.getElementById("newsDetails")
    .value
    .trim();


  if(!title || !details){

    toast("Title और Details दोनों भरें।");

    return;
  }


  try{

    if(id){

      await db.ref("news/"+id).update({

        title:title,
        details:details,
        updatedAt:Date.now()

      });

      toast("News update हो गई।");

    }else{

      await db.ref("news").push({

        title:title,
        details:details,
        createdAt:Date.now()

      });

      toast("News successfully add हो गई।");

    }

    clearNewsForm();

    renderAdminNews();

  }catch(error){

    console.error(error);

    toast("News save नहीं हुई।");

  }

});


function clearNewsForm(){

  document.getElementById("newsForm").reset();

  document.getElementById("newsEditId").value="";

  document.getElementById("newsSaveText")
    .textContent="Add News";

}


function renderAdminNews(){

  if(sessionStorage.getItem("srjmAdmin") !== "true")
    return;


  db.ref("news").once("value")
  .then(snapshot=>{

    const data = snapshot.val() || {};

    const list =
      document.getElementById("adminNewsList");

    list.innerHTML="";


    const news = Object.entries(data)
      .map(([id,item])=>({
        id,
        ...item
      }))
      .sort((a,b)=>
        Number(b.createdAt || 0) -
        Number(a.createdAt || 0)
      );


    if(news.length === 0){

      list.innerHTML=`
        <div class="admin-item">
          अभी कोई News नहीं है।
        </div>
      `;

      return;
    }


    news.forEach(item=>{

      const div =
        document.createElement("div");

      div.className="admin-item";

      div.innerHTML=`

        <h4>
          ${escapeHTML(item.title)}
        </h4>

        <div class="admin-meta">
          ${escapeHTML(formatDate(item.createdAt))}
        </div>

        <p style="white-space:pre-wrap;">
          ${escapeHTML(item.details)}
        </p>

        <div class="admin-actions">

          <button
            class="btn btn-gold"
            onclick="editNews('${item.id}')">
            Edit
          </button>

          <button
            class="btn btn-red"
            onclick="deleteNews('${item.id}')">
            Delete
          </button>

        </div>

      `;

      list.appendChild(div);

    });

  })
  .catch(error=>{

    console.error(error);

    toast("Admin News load नहीं हुई।");

  });

}


function editNews(id){

  if(sessionStorage.getItem("srjmAdmin") !== "true")
    return;


  db.ref("news/"+id).once("value")
  .then(snapshot=>{

    const item = snapshot.val();

    if(!item) return;


    document.getElementById("newsEditId")
      .value=id;

    document.getElementById("newsTitle")
      .value=item.title || "";

    document.getElementById("newsDetails")
      .value=item.details || "";

    document.getElementById("newsSaveText")
      .textContent="Update News";


    document.getElementById("newsTitle")
      .scrollIntoView({
        behavior:"smooth",
        block:"center"
      });

  });

}


async function deleteNews(id){

  if(sessionStorage.getItem("srjmAdmin") !== "true")
    return;


  if(!confirm("क्या आप इस News को delete करना चाहते हैं?"))
    return;


  try{

    await db.ref("news/"+id).remove();

    renderAdminNews();

    toast("News delete हो गई।");

  }catch(error){

    console.error(error);

    toast("News delete नहीं हुई।");

  }

}


/* =========================
   START
========================= */

loadNews();


/* Restore admin panel after refresh */

if(sessionStorage.getItem("srjmAdmin") === "true"){

  document.getElementById("adminLoginBox").style.display="none";

  document.getElementById("adminPanel").style.display="block";

  renderApplications();

  renderAdminNews();

}

</script>

</body>
</html>
