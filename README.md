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
  margin:0;
  padding:0;
}

html{
  scroll-behavior:smooth;
}

:root{
  --maroon:#54150d;
  --maroon2:#761d0e;
  --saffron:#c65b16;
  --gold:#d8a13a;
  --cream:#fffaf2;
  --paper:#fffdf9;
  --border:#eadac8;
  --text:#321b13;
  --muted:#76645b;
  --green:#28783a;
  --red:#b92b2b;
  --shadow:0 8px 28px rgba(67,30,10,.075);
}

body{
  font-family:Arial,"Noto Sans Devanagari",sans-serif;
  background:
    radial-gradient(circle at 10% 10%,rgba(216,161,58,.06),transparent 25%),
    radial-gradient(circle at 90% 30%,rgba(198,91,22,.05),transparent 25%),
    var(--cream);
  color:var(--text);
  line-height:1.6;
}

button,input,textarea,select{
  font:inherit;
}

button{
  cursor:pointer;
}

a{
  text-decoration:none;
}

/* ================= HERO ================= */

.hero{
  min-height:410px;
  position:relative;
  overflow:hidden;
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  text-align:center;
  padding:38px 16px;
  background:
    radial-gradient(circle at 50% 12%,rgba(255,222,133,.22),transparent 22%),
    linear-gradient(135deg,#430c08 0%,#68170d 48%,#9c3911 100%);
}

.hero:before,
.hero:after{
  content:"";
  position:absolute;
  border-radius:50%;
  pointer-events:none;
}

.hero:before{
  width:430px;
  height:430px;
  left:-260px;
  bottom:-280px;
  border:1px solid rgba(255,220,150,.13);
  box-shadow:
    0 0 0 35px rgba(255,255,255,.025),
    0 0 0 70px rgba(255,255,255,.02);
}

.hero:after{
  width:340px;
  height:340px;
  right:-220px;
  top:-220px;
  border:1px solid rgba(255,220,150,.13);
}

.heroContent{
  position:relative;
  z-index:2;
  width:100%;
  max-width:850px;
}

.om{
  font-size:38px;
  color:#ffe0a0;
  margin-bottom:2px;
  text-shadow:0 3px 15px rgba(0,0,0,.25);
}

/* TEMPLE */

.templeLogo{
  width:180px;
  height:122px;
  position:relative;
  margin:2px auto 15px;
  filter:drop-shadow(0 8px 12px rgba(0,0,0,.15));
}

.templeBody{
  position:absolute;
  left:31px;
  right:31px;
  bottom:5px;
  height:67px;
  background:#fff2ca;
  border:3px solid #dca02d;
}

.templeDoor{
  position:absolute;
  bottom:5px;
  left:70px;
  width:40px;
  height:53px;
  border-radius:22px 22px 0 0;
  background:#64140c;
  border:2px solid #d69a28;
}

.templeRoof{
  position:absolute;
  top:31px;
  left:21px;
  right:21px;
  height:47px;
  background:#ffd46b;
  clip-path:polygon(50% 0,100% 100%,0 100%);
}

.templeRoof2{
  position:absolute;
  top:50px;
  left:41px;
  right:41px;
  height:39px;
  background:#ffe6a0;
  clip-path:polygon(50% 0,100% 100%,0 100%);
}

.templeFlagPole{
  position:absolute;
  top:0;
  left:88px;
  width:4px;
  height:42px;
  background:#f6d079;
}

.templeFlag{
  position:absolute;
  top:3px;
  left:92px;
  width:38px;
  height:21px;
  background:#ed4019;
  clip-path:polygon(0 0,100% 25%,72% 50%,100% 75%,0 100%);
}

.hero h1{
  font-size:clamp(28px,5vw,45px);
  line-height:1.18;
  letter-spacing:.2px;
  text-shadow:0 3px 12px rgba(0,0,0,.3);
}

.heroSub{
  margin-top:8px;
  font-size:18px;
  color:#ffe4b1;
}

.location{
  margin-top:2px;
  font-size:14px;
  opacity:.86;
}

.jai{
  display:inline-flex;
  align-items:center;
  justify-content:center;
  margin-top:15px;
  padding:7px 19px;
  border:1px solid rgba(255,230,180,.35);
  border-radius:30px;
  background:rgba(255,255,255,.08);
  backdrop-filter:blur(5px);
  font-weight:bold;
  font-size:14px;
}

/* ================= NAV ================= */

nav{
  position:sticky;
  top:0;
  z-index:100;
  background:rgba(66,14,8,.97);
  border-bottom:1px solid rgba(216,161,58,.2);
  box-shadow:0 4px 18px rgba(0,0,0,.15);
}

.navInner{
  max-width:1080px;
  margin:auto;
  padding:7px 10px;
  display:flex;
  justify-content:center;
  gap:4px;
  overflow-x:auto;
  scrollbar-width:none;
}

.navInner::-webkit-scrollbar{
  display:none;
}

nav a{
  color:#fff7e9;
  white-space:nowrap;
  padding:8px 13px;
  border-radius:20px;
  font-size:13px;
  transition:.2s ease;
}

nav a:hover{
  background:rgba(216,161,58,.18);
  color:#ffd98a;
}

/* ================= COMMON ================= */

.container{
  max-width:1080px;
  margin:auto;
  padding:48px 16px;
}

.sectionHead{
  text-align:center;
  margin-bottom:24px;
}

.sectionHead .smallTitle{
  color:var(--saffron);
  font-size:11px;
  font-weight:bold;
  letter-spacing:1.5px;
  text-transform:uppercase;
}

.sectionHead h2{
  color:var(--maroon2);
  font-size:28px;
  line-height:1.25;
  margin-top:3px;
}

.sectionHead p{
  color:var(--muted);
  margin-top:5px;
  font-size:14px;
}

.card{
  background:rgba(255,255,255,.94);
  border:1px solid var(--border);
  border-radius:16px;
  box-shadow:var(--shadow);
  padding:21px;
}

.grid{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:16px;
}

/* ================= WELCOME ================= */

.welcome{
  text-align:center;
  max-width:850px;
  margin:auto;
}

.welcomeBadge{
  display:inline-block;
  padding:5px 13px;
  border-radius:20px;
  background:#fff3df;
  color:#a84b12;
  font-size:11px;
  font-weight:bold;
  letter-spacing:.7px;
  margin-bottom:9px;
}

.welcome h2{
  color:var(--maroon2);
  font-size:25px;
  line-height:1.35;
  margin-bottom:8px;
}

.welcome p{
  color:#604f46;
  font-size:14px;
}

.feature{
  text-align:center;
  padding:19px 15px;
}

.featureIcon{
  font-size:32px;
  margin-bottom:5px;
}

.feature h3{
  color:var(--maroon2);
  font-size:17px;
  margin-bottom:3px;
}

.feature p{
  color:#735f55;
  font-size:13px;
}

/* ================= NEWS ================= */

.newsGrid{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:15px;
}

.newsCard{
  border-left:4px solid var(--gold);
  padding:19px;
  transition:.2s ease;
}

.newsCard:hover{
  transform:translateY(-2px);
  box-shadow:0 11px 30px rgba(67,30,10,.10);
}

.newsDate{
  font-size:11px;
  color:#9b7d6c;
  margin-bottom:5px;
}

.newsTitle{
  color:#7b200e;
  font-size:19px;
  font-weight:bold;
  line-height:1.35;
  margin-bottom:6px;
}

.newsText{
  color:#59463d;
  font-size:14px;
  white-space:pre-wrap;
}

.readTag{
  display:inline-block;
  margin-top:10px;
  color:#b34c10;
  font-size:12px;
  font-weight:bold;
}

/* ================= FORM ================= */

.formGrid{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:13px 15px;
}

.field{
  display:flex;
  flex-direction:column;
  gap:5px;
}

.full{
  grid-column:1/-1;
}

label{
  color:#512a1d;
  font-weight:bold;
  font-size:13px;
}

input,
textarea,
select{
  width:100%;
  padding:10px 12px;
  border:1px solid #ddc9b5;
  border-radius:9px;
  background:#fffdfa;
  color:#352016;
  outline:none;
  font-size:14px;
  transition:.2s;
}

input::placeholder,
textarea::placeholder{
  color:#a18e83;
}

input:focus,
textarea:focus,
select:focus{
  border-color:#c85e15;
  box-shadow:0 0 0 3px rgba(200,94,21,.08);
}

textarea{
  min-height:100px;
  resize:vertical;
}

.supportBox{
  background:#fff8ea;
  border:1px solid #efd8b4;
  border-radius:11px;
  padding:12px;
}

.supportBox select{
  margin-top:6px;
}

.help{
  font-size:11px;
  color:#806c60;
}

.formActions{
  text-align:center;
  margin-top:18px;
}

.btn{
  border:0;
  border-radius:9px;
  padding:10px 16px;
  color:#fff;
  background:linear-gradient(135deg,#8d210e,#ca5d15);
  font-weight:bold;
  font-size:13px;
  transition:.2s ease;
  box-shadow:0 3px 8px rgba(100,35,10,.12);
}

.btn:hover{
  transform:translateY(-1px);
  box-shadow:0 6px 14px rgba(100,35,10,.18);
}

.btn.green{
  background:#287a3b;
}

.btn.red{
  background:#b92d2d;
}

.btn.gray{
  background:#555;
}

/* ================= ADMIN ================= */

.adminLogin{
  max-width:410px;
  margin:auto;
}

.adminPanel{
  display:none;
}

.adminHeader{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:15px;
  flex-wrap:wrap;
}

.adminHeader h3{
  color:var(--maroon2);
  font-size:20px;
}

.filters{
  display:flex;
  gap:9px;
  margin:14px 0;
  flex-wrap:wrap;
}

.filters input{
  flex:1;
  min-width:220px;
}

.application{
  background:#fffdfa;
  border:1px solid #ead9c8;
  border-radius:13px;
  padding:15px;
  margin-top:12px;
}

.appTop{
  display:flex;
  justify-content:space-between;
  gap:12px;
  flex-wrap:wrap;
  padding-bottom:9px;
  border-bottom:1px solid #eadfd5;
}

.appTop h3{
  color:#74200f;
  font-size:17px;
}

.status{
  display:inline-block;
  padding:4px 10px;
  border-radius:20px;
  font-size:10px;
  font-weight:bold;
  height:max-content;
}

.pending{
  background:#fff0c4;
  color:#795700;
}

.accepted{
  background:#daf3df;
  color:#17682a;
}

.rejected{
  background:#ffdddd;
  color:#981919;
}

.appInfo{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:7px 18px;
  margin-top:11px;
  font-size:13px;
}

.appInfo b{
  color:#66301d;
}

.appButtons{
  display:flex;
  gap:7px;
  flex-wrap:wrap;
  margin-top:13px;
}

/* ================= ADMIN NEWS ================= */

#adminNewsList{
  margin-top:17px;
}

#adminNewsList .application p{
  font-size:14px;
  color:#59463d;
}

/* ================= FOOTER ================= */

footer{
  background:
    linear-gradient(135deg,#350a06,#4d1009);
  color:#f5d6aa;
  text-align:center;
  padding:28px 15px;
  border-top:1px solid rgba(216,161,58,.18);
}

footer strong{
  color:#fff;
  font-size:14px;
}

footer p{
  font-size:13px;
}

/* ================= TOAST ================= */

#toast{
  position:fixed;
  z-index:500;
  left:50%;
  bottom:22px;
  transform:translate(-50%,120px);
  opacity:0;
  background:#2d1009;
  color:#fff;
  padding:10px 18px;
  border-radius:25px;
  transition:.3s;
  max-width:90%;
  text-align:center;
  font-size:13px;
  box-shadow:0 8px 25px rgba(0,0,0,.2);
}

#toast.show{
  opacity:1;
  transform:translate(-50%,0);
}

/* ================= MOBILE ================= */

@media(max-width:850px){

  .grid{
    grid-template-columns:repeat(3,1fr);
  }

}

@media(max-width:650px){

  .hero{
    min-height:385px;
    padding:30px 14px;
  }

  .om{
    font-size:32px;
  }

  .templeLogo{
    transform:scale(.9);
    margin-top:-3px;
    margin-bottom:7px;
  }

  .hero h1{
    font-size:28px;
  }

  .heroSub{
    font-size:16px;
  }

  .grid,
  .newsGrid,
  .formGrid{
    grid-template-columns:1fr;
  }

  .full{
    grid-column:auto;
  }

  .appInfo{
    grid-template-columns:1fr;
  }

  .container{
    padding:38px 12px;
  }

  .card{
    padding:17px;
    border-radius:14px;
  }

  .sectionHead{
    margin-bottom:20px;
  }

  .sectionHead h2{
    font-size:24px;
  }

  .welcome h2{
    font-size:22px;
  }

  nav a{
    padding:7px 10px;
    font-size:12px;
  }

  .navInner{
    justify-content:flex-start;
  }

  .filters{
    flex-direction:column;
  }

  .filters input{
    min-width:0;
  }

  .adminHeader{
    align-items:flex-start;
  }
}

/* ================= SMALL PHONE ================= */

@media(max-width:380px){

  .hero h1{
    font-size:25px;
  }

  .heroSub{
    font-size:15px;
  }

  .container{
    padding-left:10px;
    padding-right:10px;
  }

  .btn{
    padding:9px 13px;
    font-size:12px;
  }
}
</style>
</head>

<body>

<!-- ================= HERO ================= -->

<header class="hero" id="home">

  <div class="heroContent">

    <div class="om">ॐ</div>

    <div class="templeLogo">

      <div class="templeFlagPole"></div>
      <div class="templeFlag"></div>
      <div class="templeRoof"></div>
      <div class="templeRoof2"></div>
      <div class="templeBody"></div>
      <div class="templeDoor"></div>

    </div>

    <h1>श्री राम जानकी मंदिर</h1>

    <div class="heroSub">
      दुर्गा पूजा सेवा समिति
    </div>

    <div class="location">
      Siswa Bazar
    </div>

    <div class="jai">
      जय श्री राम 🚩
    </div>

  </div>

</header>

<!-- ================= NAVIGATION ================= -->

<nav>

  <div class="navInner">

    <a href="#home">Home</a>
    <a href="#news">Latest News</a>
    <a href="#volunteer">Volunteer</a>
    <a href="#committee">Committee</a>
    <a href="#admin">Admin Panel</a>

  </div>

</nav>

<!-- ================= WELCOME ================= -->

<section class="container">

  <div class="card welcome">

    <div class="welcomeBadge">
      OFFICIAL WEBSITE
    </div>

    <h2>
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति
    </h2>

    <p>
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति की
      official website पर आपका हार्दिक स्वागत है।
    </p>

    <p style="margin-top:6px">
      धार्मिक सेवा, सामाजिक सहयोग और मंदिर से संबंधित
      latest updates यहाँ प्राप्त करें।
    </p>

  </div>

  <div class="grid" style="margin-top:17px">

    <div class="card feature">

      <div class="featureIcon">🛕</div>

      <h3>मंदिर सेवा</h3>

      <p>
        मंदिर एवं धार्मिक कार्यक्रमों में सहयोग करें।
      </p>

    </div>

    <div class="card feature">

      <div class="featureIcon">🙏</div>

      <h3>Volunteer</h3>

      <p>
        अपनी रुचि के अनुसार सेवा में योगदान दें।
      </p>

    </div>

    <div class="card feature">

      <div class="featureIcon">🎪</div>

      <h3>दुर्गा पूजा</h3>

      <p>
        आयोजन एवं व्यवस्था में अपना सहयोग दें।
      </p>

    </div>

  </div>

</section>

<!-- ================= NEWS ================= -->

<section id="news" class="container">

  <div class="sectionHead">

    <div class="smallTitle">
      Latest Updates
    </div>

    <h2>📰 नवीनतम समाचार</h2>

    <p>
      मंदिर समिति की latest information
    </p>

  </div>

  <div id="publicNews" class="newsGrid">

    <div class="card">
      News loading...
    </div>

  </div>

</section>

<!-- ================= VOLUNTEER ================= -->

<section id="volunteer" class="container">

  <div class="sectionHead">

    <div class="smallTitle">
      Join Our Team
    </div>

    <h2>🙏 Volunteer Application</h2>

    <p>
      मंदिर सेवा के लिए अपना application submit करें।
    </p>

  </div>

  <div class="card">

    <form id="volunteerForm">

      <div class="formGrid">

        <div class="field">

          <label>पूरा नाम *</label>

          <input
            id="vName"
            required
            maxlength="100"
            placeholder="अपना पूरा नाम">

        </div>

        <div class="field">

          <label>Mobile Number *</label>

          <input
            id="vMobile"
            required
            maxlength="10"
            inputmode="numeric"
            placeholder="10 अंकों का मोबाइल नंबर">

        </div>

        <div class="field">

          <label>आयु *</label>

          <input
            id="vAge"
            required
            type="number"
            min="1"
            max="100"
            placeholder="Age">

        </div>

        <div class="field">

          <label>पता *</label>

          <input
            id="vAddress"
            required
            maxlength="250"
            placeholder="पूरा पता">

        </div>

        <div class="field full">

          <div class="supportBox">

            <label>
              आप किस प्रकार से सहयोग करना चाहते हैं? *
            </label>

            <select id="vSupport" required>

              <option value="">
                -- Select Service Type --
              </option>

              <option value="पूजा / धार्मिक सेवा">
                🛕 पूजा / धार्मिक सेवा
              </option>

              <option value="मंदिर व्यवस्था">
                🛕 मंदिर व्यवस्था
              </option>

              <option value="दुर्गा पूजा आयोजन">
                🎪 दुर्गा पूजा आयोजन
              </option>

              <option value="साफ-सफाई / व्यवस्था">
                🧹 साफ-सफाई / व्यवस्था
              </option>

              <option value="प्रचार-प्रसार">
                📢 प्रचार-प्रसार
              </option>

              <option value="सोशल मीडिया / ऑनलाइन कार्य">
                💻 Social Media / Online Work
              </option>

              <option value="आर्थिक सहयोग">
                💰 आर्थिक सहयोग
              </option>

              <option value="भोजन / प्रसाद व्यवस्था">
                🍲 भोजन / प्रसाद व्यवस्था
              </option>

              <option value="सुरक्षा / भीड़ व्यवस्था">
                🤝 सुरक्षा / भीड़ व्यवस्था
              </option>

              <option value="अन्य सेवा">
                ✨ अन्य सेवा
              </option>

            </select>

          </div>

        </div>

        <div class="field">

          <label>योगदान / Contribution</label>

          <input
            id="vContribution"
            maxlength="150"
            placeholder="समय, श्रम, आर्थिक सहयोग आदि">

        </div>

        <div class="field">

          <label>Photo URL</label>

          <input
            id="vPhoto"
            type="url"
            placeholder="https://...">

        </div>

        <div class="field full">

          <label>PDF Application Link</label>

          <input
            id="vPdf"
            type="url"
            placeholder="PDF का link">

          <div class="help">
            PDF को पहले किसी file-sharing service पर upload करके उसका link डालें।
          </div>

        </div>

        <div class="field full">

          <label>अन्य जानकारी / Message</label>

          <textarea
            id="vMessage"
            maxlength="1000"
            placeholder="अपने बारे में या सेवा से संबंधित जानकारी"></textarea>

        </div>

      </div>

      <div class="formActions">

        <button class="btn" type="submit">
          Submit Application
        </button>

      </div>

    </form>

  </div>

</section>

<!-- ================= COMMITTEE ================= -->

<section id="committee" class="container">

  <div class="sectionHead">

    <div class="smallTitle">
      Committee Membership
    </div>

    <h2>👥 समिति सदस्य आवेदन</h2>

    <p>
      समिति में शामिल होने के लिए application submit करें।
    </p>

  </div>

  <div class="card">

    <form id="committeeForm">

      <div class="formGrid">

        <div class="field">

          <label>पूरा नाम *</label>

          <input
            id="cName"
            required
            maxlength="100"
            placeholder="पूरा नाम">

        </div>

        <div class="field">

          <label>Mobile Number *</label>

          <input
            id="cMobile"
            required
            maxlength="10"
            inputmode="numeric"
            placeholder="10 अंकों का मोबाइल नंबर">

        </div>

        <div class="field">

          <label>आयु *</label>

          <input
            id="cAge"
            required
            type="number"
            min="1"
            max="100"
            placeholder="Age">

        </div>

        <div class="field">

          <label>पता *</label>

          <input
            id="cAddress"
            required
            maxlength="250"
            placeholder="पूरा पता">

        </div>

        <div class="field full">

          <label>योगदान / Experience</label>

          <input
            id="cContribution"
            maxlength="250"
            placeholder="आप किस प्रकार सहयोग कर सकते हैं?">

        </div>

        <div class="field">

          <label>Photo URL</label>

          <input
            id="cPhoto"
            type="url"
            placeholder="https://...">

        </div>

        <div class="field full">

          <label>Message</label>

          <textarea
            id="cMessage"
            maxlength="1000"
            placeholder="अन्य जानकारी"></textarea>

        </div>

      </div>

      <div class="formActions">

        <button class="btn" type="submit">
          Submit Committee Application
        </button>

      </div>

    </form>

  </div>

</section>

<!-- ================= ADMIN ================= -->

<section id="admin" class="container">

  <div class="sectionHead">

    <div class="smallTitle">
      Administration
    </div>

    <h2>🔐 Admin Panel</h2>

    <p>
      Applications और News manage करें।
    </p>

  </div>

  <div id="adminLogin" class="card adminLogin">

    <div class="field">

      <label>Admin Password</label>

      <input
        id="adminPassword"
        type="password"
        placeholder="Enter password">

    </div>

    <div class="formActions">

      <button class="btn" onclick="adminLogin()">
        Login
      </button>

    </div>

  </div>

  <div id="adminPanel" class="adminPanel">

    <div class="card">

      <div class="adminHeader">

        <div>

          <h3>Admin Dashboard</h3>

          <div class="help">
            Manage Applications • News
          </div>

        </div>

        <button
          class="btn gray"
          onclick="adminLogout()">
          Logout
        </button>

      </div>

    </div>

    <!-- APPLICATIONS -->

    <div class="card" style="margin-top:18px">

      <h3>📋 Applications</h3>

      <div class="filters">

        <input
          id="searchApplication"
          placeholder="Search by name or mobile"
          oninput="renderApplications()">

        <select
          id="statusFilter"
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

      </div>

      <div id="applicationsList">
        Applications loading...
      </div>

    </div>

    <!-- NEWS MANAGEMENT -->

    <div class="card" style="margin-top:18px">

      <h3>📰 Manage News</h3>

      <form id="newsForm" style="margin-top:14px">

        <input
          type="hidden"
          id="editNewsId">

        <div class="formGrid">

          <div class="field full">

            <label>News Title</label>

            <input
              id="newsTitle"
              required
              maxlength="150"
              placeholder="News title">

          </div>

          <div class="field full">

            <label>News Details</label>

            <textarea
              id="newsDetails"
              required
              maxlength="1000"
              placeholder="News details"></textarea>

          </div>

        </div>

        <div class="formActions">

          <button class="btn" type="submit">
            Save News
          </button>

          <button
            type="button"
            class="btn gray"
            onclick="clearNewsForm()">
            Clear
          </button>

        </div>

      </form>

      <div id="adminNewsList"></div>

    </div>

  </div>

</section>

<!-- ================= FOOTER ================= -->

<footer>

  <p>
    <strong>
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति
    </strong>
  </p>

  <p>Siswa Bazar</p>

  <p style="margin-top:6px">
    जय श्री राम 🚩
  </p>

  <p style="font-size:11px;margin-top:8px;opacity:.65">
    Official Website • Temple & Community Service
  </p>

</footer>

<div id="toast"></div>

<script>

/* =====================================================
   FIREBASE
===================================================== */

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

const db=firebase.database();

const ADMIN_PASSWORD="SRJM2026";

let isAdmin=false;


/* ================= HELPERS ================= */

function escapeHTML(value){

  if(value===undefined || value===null){
    return "";
  }

  return String(value)
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");
}


function safeURL(url){

  if(!url)return "";

  try{

    const u=new URL(url);

    if(
      u.protocol==="http:" ||
      u.protocol==="https:"
    ){
      return u.href;
    }

  }catch(e){}

  return "";
}


function showToast(message){

  const toast=document.getElementById("toast");

  toast.textContent=message;

  toast.classList.add("show");

  setTimeout(()=>{
    toast.classList.remove("show");
  },3000);

}


function currentDate(){

  return new Date().toLocaleString("hi-IN");

}


/* ================= VOLUNTEER ================= */

document
.getElementById("volunteerForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const mobile=
    document.getElementById("vMobile")
    .value.trim();

  if(!/^[0-9]{10}$/.test(mobile)){

    showToast("सही 10 अंकों का mobile number डालें।");

    return;
  }

  const support=
    document.getElementById("vSupport")
    .value;

  if(!support){

    showToast("Service Type select करें।");

    return;
  }

  const data={

    type:"volunteer",

    name:
      document.getElementById("vName")
      .value.trim(),

    mobile,

    age:
      document.getElementById("vAge")
      .value.trim(),

    address:
      document.getElementById("vAddress")
      .value.trim(),

    supportType:support,

    contribution:
      document.getElementById("vContribution")
      .value.trim(),

    photo:
      safeURL(
        document.getElementById("vPhoto")
        .value.trim()
      ),

    pdf:
      safeURL(
        document.getElementById("vPdf")
        .value.trim()
      ),

    message:
      document.getElementById("vMessage")
      .value.trim(),

    status:"pending",

    createdAt:Date.now(),

    createdText:currentDate()

  };

  try{

    await db
      .ref("applications")
      .push(data);

    showToast(
      "Application successfully submitted!"
    );

    this.reset();

  }catch(error){

    console.error(error);

    showToast(
      "Application submit नहीं हुआ।"
    );

  }

});


/* ================= COMMITTEE ================= */

document
.getElementById("committeeForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const mobile=
    document.getElementById("cMobile")
    .value.trim();

  if(!/^[0-9]{10}$/.test(mobile)){

    showToast("सही 10 अंकों का mobile number डालें।");

    return;
  }

  const data={

    type:"committee",

    name:
      document.getElementById("cName")
      .value.trim(),

    mobile,

    age:
      document.getElementById("cAge")
      .value.trim(),

    address:
      document.getElementById("cAddress")
      .value.trim(),

    contribution:
      document.getElementById("cContribution")
      .value.trim(),

    photo:
      safeURL(
        document.getElementById("cPhoto")
        .value.trim()
      ),

    message:
      document.getElementById("cMessage")
      .value.trim(),

    status:"pending",

    createdAt:Date.now(),

    createdText:currentDate()

  };

  try{

    await db
      .ref("applications")
      .push(data);

    showToast(
      "Committee application submitted!"
    );

    this.reset();

  }catch(error){

    console.error(error);

    showToast(
      "Application submit नहीं हुआ।"
    );

  }

});


/* ================= NEWS PUBLIC ================= */

function loadNews(){

  db.ref("news").on("value",snapshot=>{

    const data=snapshot.val() || {};

    const list=
      Object.entries(data)
      .map(([id,item])=>({
        id,
        ...item
      }))
      .sort((a,b)=>
        (b.createdAt||0) -
        (a.createdAt||0)
      );

    const box=
      document.getElementById("publicNews");

    if(!list.length){

      box.innerHTML=`
        <div class="card">
          अभी कोई latest news उपलब्ध नहीं है।
        </div>
      `;

      return;
    }

    box.innerHTML=list.map(item=>`

      <article class="card newsCard">

        <div class="newsDate">
          ${escapeHTML(
            item.date ||
            item.createdText ||
            ""
          )}
        </div>

        <div class="newsTitle">
          ${escapeHTML(item.title)}
        </div>

        <div class="newsText">
          ${escapeHTML(item.details)}
        </div>

        <div class="readTag">
          Read More →
        </div>

      </article>

    `).join("");

  });

}


/* ================= ADMIN ================= */

function adminLogin(){

  const password=
    document.getElementById("adminPassword")
    .value;

  if(password===ADMIN_PASSWORD){

    isAdmin=true;

    document.getElementById("adminLogin")
      .style.display="none";

    document.getElementById("adminPanel")
      .style.display="block";

    showToast("Welcome Admin!");

    renderApplications();

    renderAdminNews();

  }else{

    showToast("Incorrect password.");

  }

}


function adminLogout(){

  isAdmin=false;

  document.getElementById("adminLogin")
    .style.display="block";

  document.getElementById("adminPanel")
    .style.display="none";

  document.getElementById("adminPassword")
    .value="";

}


/* ================= APPLICATIONS ================= */

function renderApplications(){

  if(!isAdmin)return;

  db.ref("applications")
    .once("value")
    .then(snapshot=>{

      const data=snapshot.val() || {};

      let list=
        Object.entries(data)
        .map(([id,item])=>({
          id,
          ...item
        }))
        .sort((a,b)=>
          (b.createdAt||0) -
          (a.createdAt||0)
        );

      const search=
        document.getElementById(
          "searchApplication"
        ).value.trim().toLowerCase();

      const filter=
        document.getElementById(
          "statusFilter"
        ).value;

      list=list.filter(item=>{

        const searchMatch=
          !search ||
          String(item.name||"")
          .toLowerCase()
          .includes(search) ||
          String(item.mobile||"")
          .includes(search);

        const statusMatch=
          filter==="all" ||
          (item.status||"pending")===filter;

        return searchMatch && statusMatch;

      });

      const box=
        document.getElementById(
          "applicationsList"
        );

      if(!list.length){

        box.innerHTML=`
          <div class="application">
            No applications found.
          </div>
        `;

        return;
      }

      box.innerHTML=list.map(item=>{

        const status=
          item.status||"pending";

        const photo=
          safeURL(item.photo);

        const pdf=
          safeURL(item.pdf);

        return`

          <div class="application">

            <div class="appTop">

              <div>

                <h3>
                  ${escapeHTML(item.name)}
                </h3>

                <div class="help">
                  ${
                    item.type==="committee"
                    ? "👥 Committee Member"
                    : "🙏 Volunteer"
                  }
                </div>

              </div>

              <span class="status ${status}">
                ${status.toUpperCase()}
              </span>

            </div>

            <div class="appInfo">

              <div>
                <b>Mobile:</b>
                ${escapeHTML(item.mobile)}
              </div>

              <div>
                <b>Age:</b>
                ${escapeHTML(item.age)}
              </div>

              <div>
                <b>Address:</b>
                ${escapeHTML(item.address)}
              </div>

              ${
                item.supportType
                ? `
                <div>
                  <b>Service:</b>
                  ${escapeHTML(item.supportType)}
                </div>
                `
                :""
              }

              <div>
                <b>Contribution:</b>
                ${escapeHTML(
                  item.contribution||"-"
                )}
              </div>

              <div>
                <b>Applied:</b>
                ${escapeHTML(
                  item.createdText||"-"
                )}
              </div>

            </div>

            ${
              item.message
              ? `
              <div style="margin-top:10px">
                <b>Message:</b><br>
                ${escapeHTML(item.message)}
              </div>
              `
              :""
            }

            ${
              photo
              ? `
              <div style="margin-top:9px">
                <a
                  href="${photo}"
                  target="_blank"
                  rel="noopener">
                  📷 View Photo
                </a>
              </div>
              `
              :""
            }

            ${
              pdf
              ? `
              <div style="margin-top:6px">
                <a
                  href="${pdf}"
                  target="_blank"
                  rel="noopener">
                  📄 Open PDF
                </a>
              </div>
              `
              :""
            }

            <div class="appButtons">

              ${
                status!=="accepted"
                ? `
                <button
                  class="btn green"
                  onclick="updateApplication(
                    '${item.id}',
                    'accepted'
                  )">
                  ✓ Accept
                </button>
                `
                :""
              }

              ${
                status!=="rejected"
                ? `
                <button
                  class="btn red"
                  onclick="updateApplication(
                    '${item.id}',
                    'rejected'
                  )">
                  ✕ Reject
                </button>
                `
                :""
              }

              <button
                class="btn gray"
                onclick="deleteApplication(
                  '${item.id}'
                )">
                Delete
              </button>

            </div>

          </div>

        `;

      }).join("");

    })
    .catch(error=>{

      console.error(error);

      document.getElementById(
        "applicationsList"
      ).innerHTML=`
        <div class="application">
          Applications load नहीं हो पाए।
        </div>
      `;

    });

}


function updateApplication(id,status){

  db.ref("applications/"+id)
    .update({
      status,
      updatedAt:Date.now()
    })
    .then(()=>{

      showToast(
        status==="accepted"
        ? "Application Accepted"
        : "Application Rejected"
      );

      renderApplications();

    })
    .catch(error=>{

      console.error(error);

      showToast("Status update नहीं हुआ।");

    });

}


function deleteApplication(id){

  if(!confirm(
    "क्या आप यह application delete करना चाहते हैं?"
  )){
    return;
  }

  db.ref("applications/"+id)
    .remove()
    .then(()=>{

      showToast("Application deleted");

      renderApplications();

    })
    .catch(error=>{

      console.error(error);

      showToast("Delete नहीं हुआ।");

    });

}


/* ================= NEWS ADMIN ================= */

document
.getElementById("newsForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  if(!isAdmin)return;

  const id=
    document.getElementById("editNewsId")
    .value;

  const title=
    document.getElementById("newsTitle")
    .value.trim();

  const details=
    document.getElementById("newsDetails")
    .value.trim();

  if(!title || !details){

    showToast("Title और Details भरें।");

    return;

  }

  const data={

    title,

    details,

    date:currentDate(),

    updatedAt:Date.now()

  };

  try{

    if(id){

      await db.ref("news/"+id)
        .update(data);

      showToast("News updated!");

    }else{

      data.createdAt=Date.now();

      await db.ref("news")
        .push(data);

      showToast("News added!");

    }

    clearNewsForm();

    renderAdminNews();

  }catch(error){

    console.error(error);

    showToast("News save नहीं हुई।");

  }

});


function clearNewsForm(){

  document.getElementById("editNewsId").value="";

  document.getElementById("newsTitle").value="";

  document.getElementById("newsDetails").value="";

}


function renderAdminNews(){

  if(!isAdmin)return;

  db.ref("news")
    .once("value")
    .then(snapshot=>{

      const data=snapshot.val() || {};

      const list=
        Object.entries(data)
        .map(([id,item])=>({
          id,
          ...item
        }))
        .sort((a,b)=>
          (b.createdAt||0) -
          (a.createdAt||0)
        );

      const box=
        document.getElementById(
          "adminNewsList"
        );

      if(!list.length){

        box.innerHTML=`
          <p class="help" style="margin-top:18px">
            अभी कोई news नहीं है।
          </p>
        `;

        return;
      }

      box.innerHTML=list.map(item=>`

        <div class="application">

          <h3>
            ${escapeHTML(item.title)}
          </h3>

          <div class="help">
            ${escapeHTML(item.date||"")}
          </div>

          <p style="
            margin-top:7px;
            white-space:pre-wrap">
            ${escapeHTML(item.details)}
          </p>

          <div class="appButtons">

            <button
              class="btn"
              onclick="editNews('${item.id}')">
              Edit
            </button>

            <button
              class="btn red"
              onclick="deleteNews('${item.id}')">
              Delete
            </button>

          </div>

        </div>

      `).join("");

    });

}


function editNews(id){

  db.ref("news/"+id)
    .once("value")
    .then(snapshot=>{

      const item=snapshot.val();

      if(!item)return;

      document.getElementById(
        "editNewsId"
      ).value=id;

      document.getElementById(
        "newsTitle"
      ).value=item.title||"";

      document.getElementById(
        "newsDetails"
      ).value=item.details||"";

      document.getElementById(
        "newsTitle"
      ).scrollIntoView({
        behavior:"smooth",
        block:"center"
      });

    });

}


function deleteNews(id){

  if(!confirm(
    "क्या आप यह news delete करना चाहते हैं?"
  )){
    return;
  }

  db.ref("news/"+id)
    .remove()
    .then(()=>{

      showToast("News deleted!");

      renderAdminNews();

    })
    .catch(error=>{

      console.error(error);

      showToast("News delete नहीं हुई।");

    });

}


/* ================= START ================= */

loadNews();

</script>

</body>
</html>
