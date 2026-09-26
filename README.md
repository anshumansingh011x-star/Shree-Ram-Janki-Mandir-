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

body{
  font-family:Arial,"Noto Sans Devanagari",sans-serif;
  background:#fff8ed;
  color:#351b0d;
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
  color:inherit;
}

/* HEADER */

header{
  position:relative;
  overflow:hidden;
  min-height:430px;
  background:
    radial-gradient(circle at 50% 18%,rgba(255,239,181,.9),transparent 22%),
    linear-gradient(145deg,#7b160d,#c43c12 48%,#f28b18);
  color:white;
  display:flex;
  align-items:center;
  justify-content:center;
  text-align:center;
  padding:35px 18px;
}

header:before,
header:after{
  content:"";
  position:absolute;
  border-radius:50%;
  background:rgba(255,255,255,.08);
}

header:before{
  width:320px;
  height:320px;
  left:-120px;
  bottom:-150px;
}

header:after{
  width:280px;
  height:280px;
  right:-100px;
  top:-130px;
}

.hero{
  position:relative;
  z-index:2;
  width:100%;
  max-width:1000px;
}

.om{
  font-size:52px;
  margin-bottom:5px;
  text-shadow:0 3px 12px rgba(0,0,0,.3);
}

.heroTemple{
  width:230px;
  height:150px;
  margin:8px auto 18px;
  position:relative;
}

/* Custom temple illustration */

.templeRoof{
  position:absolute;
  left:35px;
  right:35px;
  top:38px;
  height:20px;
  background:#ffd36b;
  clip-path:polygon(50% 0,100% 100%,0 100%);
  filter:drop-shadow(0 4px 3px rgba(0,0,0,.25));
}

.templeRoof2{
  position:absolute;
  left:55px;
  right:55px;
  top:60px;
  height:15px;
  background:#ffe39b;
  clip-path:polygon(50% 0,100% 100%,0 100%);
}

.templeBody{
  position:absolute;
  left:42px;
  right:42px;
  top:73px;
  bottom:10px;
  background:#fff1c7;
  border:4px solid #e8a329;
  border-bottom:0;
}

.templeDoor{
  position:absolute;
  left:91px;
  width:48px;
  height:70px;
  bottom:0;
  background:#7b160d;
  border-radius:25px 25px 0 0;
  border:3px solid #e5a02b;
}

.templeFlag{
  position:absolute;
  width:5px;
  height:60px;
  background:#f7d27b;
  left:113px;
  top:0;
}

.templeFlag:after{
  content:"";
  position:absolute;
  top:2px;
  left:4px;
  border-top:13px solid transparent;
  border-bottom:13px solid transparent;
  border-left:35px solid #e33b18;
}

.hero h1{
  font-size:clamp(28px,6vw,48px);
  line-height:1.2;
  text-shadow:0 3px 8px rgba(0,0,0,.3);
}

.hero p{
  margin-top:8px;
  font-size:18px;
  opacity:.95;
}

.jai{
  margin-top:14px;
  display:inline-block;
  padding:8px 20px;
  border:1px solid rgba(255,255,255,.5);
  border-radius:30px;
  background:rgba(255,255,255,.12);
  font-weight:bold;
}

/* NAV */

nav{
  position:sticky;
  top:0;
  z-index:50;
  background:#4d120c;
  box-shadow:0 3px 12px rgba(0,0,0,.18);
}

.navInner{
  max-width:1100px;
  margin:auto;
  display:flex;
  justify-content:center;
  gap:4px;
  overflow-x:auto;
  padding:8px;
}

nav a{
  color:white;
  padding:9px 13px;
  border-radius:20px;
  white-space:nowrap;
  font-size:14px;
}

nav a:hover{
  background:#d66a17;
}

/* COMMON */

.container{
  max-width:1100px;
  margin:auto;
  padding:55px 16px;
}

.sectionTitle{
  text-align:center;
  color:#8d230f;
  margin-bottom:28px;
}

.sectionTitle h2{
  font-size:30px;
}

.sectionTitle p{
  color:#72584b;
  margin-top:5px;
}

.card{
  background:white;
  border-radius:18px;
  padding:22px;
  box-shadow:0 5px 22px rgba(91,40,10,.1);
  border:1px solid #f1dfca;
}

.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:20px;
}

/* HOME */

.welcome{
  text-align:center;
  font-size:19px;
}

.feature{
  text-align:center;
}

.featureIcon{
  font-size:40px;
  margin-bottom:8px;
}

/* FORMS */

.formGrid{
  display:grid;
  grid-template-columns:repeat(2,1fr);
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
  font-weight:bold;
  color:#542718;
}

input,
textarea,
select{
  width:100%;
  border:1px solid #dfc7b0;
  background:#fffdf9;
  border-radius:10px;
  padding:12px;
  outline:none;
}

input:focus,
textarea:focus,
select:focus{
  border-color:#d56b18;
  box-shadow:0 0 0 3px rgba(213,107,24,.1);
}

textarea{
  min-height:100px;
  resize:vertical;
}

.btn{
  border:0;
  border-radius:10px;
  padding:11px 18px;
  font-weight:bold;
  color:white;
  background:linear-gradient(135deg,#a52a10,#e27517);
}

.btn:hover{
  transform:translateY(-1px);
}

.btn.secondary{
  background:#555;
}

.btn.green{
  background:#218838;
}

.btn.red{
  background:#c62828;
}

.formActions{
  margin-top:18px;
  text-align:center;
}

.help{
  font-size:13px;
  color:#775f52;
  margin-top:4px;
}

/* SELECT SPECIAL */

.supportBox{
  background:#fff6e5;
  border:1px solid #f0d3a3;
  border-radius:12px;
  padding:14px;
}

/* NEWS */

.newsCard{
  border-left:5px solid #d86b16;
}

.newsDate{
  font-size:12px;
  color:#927467;
  margin-bottom:5px;
}

.newsTitle{
  color:#8c230e;
  font-size:21px;
  margin-bottom:8px;
}

.newsText{
  white-space:pre-wrap;
}

.newsButtons{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  margin-top:15px;
}

/* GALLERY */

.galleryGrid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
  gap:18px;
}

.galleryItem{
  overflow:hidden;
  border-radius:16px;
  background:white;
  box-shadow:0 4px 18px rgba(70,30,10,.13);
}

.galleryItem img{
  width:100%;
  height:220px;
  object-fit:cover;
  display:block;
}

.galleryCaption{
  padding:12px;
  text-align:center;
  font-weight:bold;
}

/* DEFAULT TEMPLE CARD */

.templeCard{
  height:220px;
  background:
    radial-gradient(circle at 50% 35%,#fff0a8 0 7%,transparent 8%),
    linear-gradient(#e9771a,#9e1e0e);
  position:relative;
  overflow:hidden;
}

.templeCard .miniTemple{
  position:absolute;
  left:15%;
  right:15%;
  bottom:20px;
  height:130px;
  background:#fff0c8;
  border:5px solid #e4a126;
}

.miniTemple:before{
  content:"";
  position:absolute;
  left:10%;
  right:10%;
  top:-55px;
  height:65px;
  background:#ffd875;
  clip-path:polygon(50% 0,100% 100%,0 100%);
}

.miniTemple:after{
  content:"";
  position:absolute;
  left:42%;
  width:16%;
  bottom:0;
  height:75px;
  background:#76170d;
  border-radius:30px 30px 0 0;
}

/* ADMIN */

.adminPanel{
  display:none;
}

.adminLogin{
  max-width:430px;
  margin:auto;
}

.adminTop{
  display:flex;
  justify-content:space-between;
  gap:10px;
  flex-wrap:wrap;
  margin-bottom:20px;
}

.filters{
  display:flex;
  gap:10px;
  flex-wrap:wrap;
  margin-bottom:18px;
}

.filters input{
  flex:1;
  min-width:220px;
}

.application{
  border:1px solid #ead7c5;
  border-radius:14px;
  padding:17px;
  margin-bottom:15px;
  background:#fffdfa;
}

.appHead{
  display:flex;
  justify-content:space-between;
  gap:10px;
  flex-wrap:wrap;
  border-bottom:1px solid #eadfd5;
  padding-bottom:10px;
  margin-bottom:10px;
}

.status{
  display:inline-block;
  padding:4px 10px;
  border-radius:20px;
  font-size:12px;
  font-weight:bold;
}

.status.pending{
  background:#fff0c2;
  color:#825b00;
}

.status.accepted{
  background:#d9f5df;
  color:#176b27;
}

.status.rejected{
  background:#ffdede;
  color:#9b1717;
}

.appInfo{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:6px 20px;
}

.appInfo b{
  color:#6b311e;
}

.appButtons{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  margin-top:15px;
}

/* ADMIN NEWS */

.adminNews{
  margin-top:30px;
}

/* FOOTER */

footer{
  background:#3c0e09;
  color:#ffe7c1;
  text-align:center;
  padding:30px 15px;
  margin-top:20px;
}

footer strong{
  color:white;
}

/* MESSAGE */

#toast{
  position:fixed;
  left:50%;
  bottom:25px;
  transform:translateX(-50%) translateY(100px);
  background:#32150e;
  color:white;
  padding:12px 20px;
  border-radius:30px;
  z-index:100;
  opacity:0;
  transition:.3s;
  max-width:90%;
  text-align:center;
}

#toast.show{
  opacity:1;
  transform:translateX(-50%) translateY(0);
}

/* MOBILE */

@media(max-width:700px){
  .formGrid{
    grid-template-columns:1fr;
  }

  .field.full{
    grid-column:auto;
  }

  .appInfo{
    grid-template-columns:1fr;
  }

  header{
    min-height:400px;
  }

  .container{
    padding:40px 12px;
  }

  .heroTemple{
    transform:scale(.85);
    margin-top:0;
    margin-bottom:0;
  }
}
</style>
</head>

<body>

<!-- ================= HEADER ================= -->

<header id="home">
  <div class="hero">

    <div class="om">ॐ</div>

    <div class="heroTemple">
      <div class="templeFlag"></div>
      <div class="templeRoof"></div>
      <div class="templeRoof2"></div>
      <div class="templeBody"></div>
      <div class="templeDoor"></div>
    </div>

    <h1>श्री राम जानकी मंदिर</h1>

    <p>
      दुर्गा पूजा सेवा समिति • Siswa Bazar
    </p>

    <div class="jai">
      जय श्री राम 🚩
    </div>

  </div>
</header>

<!-- ================= NAV ================= -->

<nav>
  <div class="navInner">
    <a href="#home">होम</a>
    <a href="#news">📰 समाचार</a>
    <a href="#gallery">🖼️ गैलरी</a>
    <a href="#volunteer">🙏 स्वयंसेवक</a>
    <a href="#committee">👥 समिति</a>
    <a href="#admin">🔐 Admin</a>
  </div>
</nav>

<!-- ================= HOME ================= -->

<section class="container">

  <div class="sectionTitle">
    <h2>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h2>
    <p>Siswa Bazar</p>
  </div>

  <div class="card welcome">
    <p>
      <b>जय श्री राम 🚩</b>
    </p>

    <p style="margin-top:10px">
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति की
      आधिकारिक वेबसाइट पर आपका हार्दिक स्वागत है।
    </p>

    <p style="margin-top:8px">
      धार्मिक सेवा, सामाजिक सहयोग एवं मंदिर से संबंधित
      नवीनतम जानकारी यहाँ प्राप्त करें।
    </p>
  </div>

  <div class="grid" style="margin-top:22px">

    <div class="card feature">
      <div class="featureIcon">🛕</div>
      <h3>मंदिर सेवा</h3>
      <p>मंदिर एवं धार्मिक कार्यक्रमों में सहयोग करें।</p>
    </div>

    <div class="card feature">
      <div class="featureIcon">🙏</div>
      <h3>स्वयंसेवक बनें</h3>
      <p>अपनी रुचि के अनुसार सेवा में योगदान दें।</p>
    </div>

    <div class="card feature">
      <div class="featureIcon">🎪</div>
      <h3>दुर्गा पूजा</h3>
      <p>आयोजन एवं व्यवस्थाओं में अपना सहयोग दें।</p>
    </div>

  </div>

</section>

<!-- ================= NEWS ================= -->

<section id="news" class="container">

  <div class="sectionTitle">
    <h2>📰 समाचार एवं अपडेट</h2>
    <p>मंदिर समिति की नवीनतम जानकारी</p>
  </div>

  <div id="publicNews" class="grid">
    <div class="card">
      समाचार लोड हो रहे हैं...
    </div>
  </div>

</section>

<!-- ================= GALLERY ================= -->

<section id="gallery" class="container">

  <div class="sectionTitle">
    <h2>🖼️ मंदिर गैलरी</h2>
    <p>श्री राम जानकी मंदिर एवं समिति की झलकियाँ</p>
  </div>

  <div id="galleryGrid" class="galleryGrid"></div>

</section>

<!-- ================= VOLUNTEER ================= -->

<section id="volunteer" class="container">

  <div class="sectionTitle">
    <h2>🙏 स्वयंसेवक आवेदन</h2>
    <p>मंदिर सेवा के लिए अपना आवेदन जमा करें</p>
  </div>

  <div class="card">

    <form id="volunteerForm">

      <div class="formGrid">

        <div class="field">
          <label>पूरा नाम *</label>
          <input id="vName" required maxlength="100"
                 placeholder="अपना पूरा नाम">
        </div>

        <div class="field">
          <label>मोबाइल नंबर *</label>
          <input id="vMobile"
                 required
                 maxlength="10"
                 inputmode="numeric"
                 placeholder="10 अंकों का मोबाइल नंबर">
        </div>

        <div class="field">
          <label>आयु *</label>
          <input id="vAge"
                 required
                 type="number"
                 min="1"
                 max="100"
                 placeholder="आयु">
        </div>

        <div class="field">
          <label>पता *</label>
          <input id="vAddress"
                 required
                 maxlength="250"
                 placeholder="पूरा पता">
        </div>

        <!-- NEW SUPPORT TYPE -->

        <div class="field full">
          <div class="supportBox">

            <label>
              आप किस प्रकार से सहयोग करना चाहते हैं? *
            </label>

            <select id="vSupport" required>
              <option value="">
                -- सहयोग का प्रकार चुनें --
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
                💻 सोशल मीडिया / ऑनलाइन कार्य
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
          <label>आप कितना योगदान देना चाहते हैं?</label>

          <input id="vContribution"
                 maxlength="150"
                 placeholder="जैसे समय, श्रम, आर्थिक सहयोग आदि">
        </div>

        <div class="field">
          <label>फोटो का लिंक</label>

          <input id="vPhoto"
                 type="url"
                 placeholder="https://...">
        </div>

        <div class="field full">
          <label>आवेदन / दस्तावेज PDF लिंक</label>

          <input id="vPdf"
                 type="url"
                 placeholder="Google Drive आदि का PDF लिंक">

          <div class="help">
            PDF पहले किसी file-sharing service पर upload करके उसका link यहाँ डालें।
          </div>
        </div>

        <div class="field full">
          <label>अन्य जानकारी / संदेश</label>

          <textarea id="vMessage"
                    maxlength="1000"
                    placeholder="अपने बारे में या सेवा से संबंधित जानकारी"></textarea>
        </div>

      </div>

      <div class="formActions">

        <button class="btn" type="submit">
          आवेदन जमा करें
        </button>

      </div>

    </form>

  </div>

</section>

<!-- ================= COMMITTEE ================= -->

<section id="committee" class="container">

  <div class="sectionTitle">
    <h2>👥 समिति सदस्य आवेदन</h2>
    <p>समिति में शामिल होने के लिए आवेदन करें</p>
  </div>

  <div class="card">

    <form id="committeeForm">

      <div class="formGrid">

        <div class="field">
          <label>पूरा नाम *</label>
          <input id="cName"
                 required
                 maxlength="100"
                 placeholder="पूरा नाम">
        </div>

        <div class="field">
          <label>मोबाइल नंबर *</label>
          <input id="cMobile"
                 required
                 maxlength="10"
                 inputmode="numeric"
                 placeholder="10 अंकों का मोबाइल नंबर">
        </div>

        <div class="field">
          <label>आयु *</label>
          <input id="cAge"
                 required
                 type="number"
                 min="1"
                 max="100"
                 placeholder="आयु">
        </div>

        <div class="field">
          <label>पता *</label>
          <input id="cAddress"
                 required
                 maxlength="250"
                 placeholder="पूरा पता">
        </div>

        <div class="field full">
          <label>योगदान / अनुभव</label>
          <input id="cContribution"
                 maxlength="250"
                 placeholder="आप किस प्रकार सहयोग कर सकते हैं?">
        </div>

        <div class="field">
          <label>फोटो का लिंक</label>
          <input id="cPhoto"
                 type="url"
                 placeholder="https://...">
        </div>

        <div class="field full">
          <label>अन्य जानकारी</label>

          <textarea id="cMessage"
                    maxlength="1000"
                    placeholder="अन्य जानकारी"></textarea>
        </div>

      </div>

      <div class="formActions">

        <button class="btn" type="submit">
          समिति आवेदन जमा करें
        </button>

      </div>

    </form>

  </div>

</section>

<!-- ================= ADMIN ================= -->

<section id="admin" class="container">

  <div class="sectionTitle">
    <h2>🔐 Admin Panel</h2>
    <p>समिति प्रशासन</p>
  </div>

  <!-- LOGIN -->

  <div id="adminLogin" class="card adminLogin">

    <div class="field">
      <label>Admin Password</label>

      <input id="adminPassword"
             type="password"
             placeholder="Admin password">
    </div>

    <div class="formActions">

      <button class="btn" onclick="adminLogin()">
        Login
      </button>

    </div>

  </div>

  <!-- ADMIN PANEL -->

  <div id="adminPanel" class="adminPanel">

    <div class="adminTop">

      <div>
        <h3>Admin Dashboard</h3>
        <p class="help">
          Applications, News और Gallery manage करें।
        </p>
      </div>

      <button class="btn secondary" onclick="adminLogout()">
        Logout
      </button>

    </div>

    <!-- APPLICATIONS -->

    <div class="card">

      <h3>📋 Applications</h3>

      <div class="filters" style="margin-top:15px">

        <input id="searchApplication"
               placeholder="नाम या मोबाइल से search करें"
               oninput="renderApplications()">

        <select id="statusFilter"
                onchange="renderApplications()">

          <option value="all">सभी</option>
          <option value="pending">Pending</option>
          <option value="accepted">Accepted</option>
          <option value="rejected">Rejected</option>

        </select>

      </div>

      <div id="applicationsList">
        Applications loading...
      </div>

    </div>

    <!-- ADD NEWS -->

    <div class="card adminNews">

      <h3>📰 Add / Edit News</h3>

      <form id="newsForm" style="margin-top:15px">

        <input type="hidden" id="editNewsId">

        <div class="formGrid">

          <div class="field full">

            <label>News Title *</label>

            <input id="newsTitle"
                   required
                   maxlength="150"
                   placeholder="समाचार का शीर्षक">

          </div>

          <div class="field full">

            <label>News Details *</label>

            <textarea id="newsDetails"
                      required
                      maxlength="1000"
                      placeholder="समाचार का विवरण"></textarea>

          </div>

        </div>

        <div class="formActions">

          <button class="btn" type="submit">
            Save News
          </button>

          <button type="button"
                  class="btn secondary"
                  onclick="clearNewsForm()">
            Clear
          </button>

        </div>

      </form>

      <div id="adminNewsList" style="margin-top:25px"></div>

    </div>

    <!-- ADD GALLERY -->

    <div class="card adminNews">

      <h3>🖼️ Gallery Image URL</h3>

      <form id="galleryForm" style="margin-top:15px">

        <div class="field">

          <label>Image URL</label>

          <input id="galleryUrl"
                 type="url"
                 required
                 placeholder="https://...">

        </div>

        <div class="field" style="margin-top:12px">

          <label>Caption</label>

          <input id="galleryCaption"
                 maxlength="100"
                 placeholder="फोटो का नाम">

        </div>

        <div class="formActions">

          <button class="btn" type="submit">
            Gallery में Add करें
          </button>

        </div>

      </form>

    </div>

  </div>

</section>

<!-- ================= FOOTER ================= -->

<footer>

  <p>
    <strong>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</strong>
  </p>

  <p>Siswa Bazar</p>

  <p style="margin-top:8px">
    जय श्री राम 🚩
  </p>

</footer>

<div id="toast"></div>

<script>

/* =====================================================
   FIREBASE CONFIG
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

const db = firebase.database();


/* =====================================================
   ADMIN PASSWORD
===================================================== */

const ADMIN_PASSWORD = "SRJM2026";

let isAdmin = false;


/* =====================================================
   HELPERS
===================================================== */

function escapeHTML(value){

  if(value === undefined || value === null){
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

  if(!url){
    return "";
  }

  try{

    const u = new URL(url);

    if(u.protocol === "http:" || u.protocol === "https:"){
      return u.href;
    }

  }catch(e){}

  return "";
}


function showToast(message){

  const toast = document.getElementById("toast");

  toast.textContent = message;

  toast.classList.add("show");

  setTimeout(()=>{
    toast.classList.remove("show");
  },3000);
}


function now(){

  return new Date().toLocaleString("hi-IN");
}


/* =====================================================
   VOLUNTEER APPLICATION
===================================================== */

document.getElementById("volunteerForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const mobile =
    document.getElementById("vMobile").value.trim();

  if(!/^[0-9]{10}$/.test(mobile)){

    showToast("कृपया सही 10 अंकों का मोबाइल नंबर डालें।");

    return;
  }

  const support =
    document.getElementById("vSupport").value;

  if(!support){

    showToast("कृपया सहयोग का प्रकार चुनें।");

    return;
  }

  const data = {

    type:"volunteer",

    name:
      document.getElementById("vName").value.trim(),

    mobile:mobile,

    age:
      document.getElementById("vAge").value.trim(),

    address:
      document.getElementById("vAddress").value.trim(),

    supportType:support,

    contribution:
      document.getElementById("vContribution").value.trim(),

    photo:
      safeURL(document.getElementById("vPhoto").value.trim()),

    pdf:
      safeURL(document.getElementById("vPdf").value.trim()),

    message:
      document.getElementById("vMessage").value.trim(),

    status:"pending",

    createdAt:Date.now(),

    createdText:now()

  };

  try{

    await db.ref("applications").push(data);

    showToast("आपका Volunteer आवेदन सफलतापूर्वक जमा हो गया।");

    this.reset();

  }catch(error){

    console.error(error);

    showToast("आवेदन जमा नहीं हो पाया। Firebase rules check करें।");

  }

});


/* =====================================================
   COMMITTEE APPLICATION
===================================================== */

document.getElementById("committeeForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  const mobile =
    document.getElementById("cMobile").value.trim();

  if(!/^[0-9]{10}$/.test(mobile)){

    showToast("कृपया सही 10 अंकों का मोबाइल नंबर डालें।");

    return;
  }

  const data = {

    type:"committee",

    name:
      document.getElementById("cName").value.trim(),

    mobile:mobile,

    age:
      document.getElementById("cAge").value.trim(),

    address:
      document.getElementById("cAddress").value.trim(),

    contribution:
      document.getElementById("cContribution").value.trim(),

    photo:
      safeURL(document.getElementById("cPhoto").value.trim()),

    message:
      document.getElementById("cMessage").value.trim(),

    status:"pending",

    createdAt:Date.now(),

    createdText:now()

  };

  try{

    await db.ref("applications").push(data);

    showToast("Committee आवेदन सफलतापूर्वक जमा हो गया।");

    this.reset();

  }catch(error){

    console.error(error);

    showToast("आवेदन जमा नहीं हो पाया।");

  }

});


/* =====================================================
   PUBLIC NEWS
===================================================== */

function loadNews(){

  db.ref("news").on("value",snapshot=>{

    const data = snapshot.val() || {};

    const list =
      Object.entries(data)
      .map(([id,item])=>({
        id,
        ...item
      }))
      .sort((a,b)=>
        (b.createdAt || 0) -
        (a.createdAt || 0)
      );

    const box =
      document.getElementById("publicNews");

    if(!list.length){

      box.innerHTML = `
        <div class="card">
          अभी कोई समाचार उपलब्ध नहीं है।
        </div>
      `;

      return;
    }

    box.innerHTML = list.map(item=>`

      <article class="card newsCard">

        <div class="newsDate">
          ${escapeHTML(item.date || item.createdText || "")}
        </div>

        <div class="newsTitle">
          ${escapeHTML(item.title)}
        </div>

        <div class="newsText">
          ${escapeHTML(item.details)}
        </div>

      </article>

    `).join("");

  },error=>{

    console.error(error);

    document.getElementById("publicNews").innerHTML = `
      <div class="card">
        समाचार लोड नहीं हो सके।
      </div>
    `;

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

    document.getElementById("adminLogin").style.display="none";

    document.getElementById("adminPanel").style.display="block";

    showToast("Admin Login सफल।");

    renderApplications();

    renderAdminNews();

  }else{

    showToast("गलत Admin Password।");

  }

}


function adminLogout(){

  isAdmin = false;

  document.getElementById("adminLogin").style.display="block";

  document.getElementById("adminPanel").style.display="none";

  document.getElementById("adminPassword").value="";

}


/* =====================================================
   APPLICATIONS
===================================================== */

function renderApplications(){

  if(!isAdmin){
    return;
  }

  db.ref("applications").once("value")
  .then(snapshot=>{

    const data = snapshot.val() || {};

    let list =
      Object.entries(data)
      .map(([id,item])=>({
        id,
        ...item
      }))
      .sort((a,b)=>
        (b.createdAt || 0) -
        (a.createdAt || 0)
      );

    const search =
      document.getElementById("searchApplication")
      .value
      .trim()
      .toLowerCase();

    const filter =
      document.getElementById("statusFilter").value;

    list = list.filter(item=>{

      const matchesSearch =
        !search ||
        String(item.name || "")
        .toLowerCase()
        .includes(search) ||

        String(item.mobile || "")
        .includes(search);

      const matchesStatus =
        filter === "all" ||
        (item.status || "pending") === filter;

      return matchesSearch && matchesStatus;

    });

    const box =
      document.getElementById("applicationsList");

    if(!list.length){

      box.innerHTML = `
        <div class="card" style="margin-top:15px">
          कोई application नहीं मिली।
        </div>
      `;

      return;
    }

    box.innerHTML = list.map(item=>{

      const status =
        item.status || "pending";

      const photo =
        safeURL(item.photo);

      const pdf =
        safeURL(item.pdf);

      return `

      <div class="application">

        <div class="appHead">

          <div>

            <h3>
              ${escapeHTML(item.name)}
            </h3>

            <div class="help">
              ${item.type === "committee"
                ? "👥 Committee Member"
                : "🙏 Volunteer"}
            </div>

          </div>

          <span class="status ${escapeHTML(status)}">
            ${escapeHTML(status.toUpperCase())}
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
              <b>सहयोग:</b>
              ${escapeHTML(item.supportType)}
            </div>
            `
            : ""
          }

          <div>
            <b>Contribution:</b>
            ${escapeHTML(item.contribution || "-")}
          </div>

          <div>
            <b>Applied:</b>
            ${escapeHTML(item.createdText || "-")}
          </div>

        </div>

        ${
          item.message
          ? `
          <div style="margin-top:12px">
            <b>Message:</b><br>
            ${escapeHTML(item.message)}
          </div>
          `
          : ""
        }

        ${
          photo
          ? `
          <div style="margin-top:12px">
            <a
              href="${photo}"
              target="_blank"
              rel="noopener">
              📷 View Photo
            </a>
          </div>
          `
          : ""
        }

        ${
          pdf
          ? `
          <div style="margin-top:8px">
            <a
              href="${pdf}"
              target="_blank"
              rel="noopener">
              📄 Open PDF Application
            </a>
          </div>
          `
          : ""
        }

        <div class="appButtons">

          ${
            status !== "accepted"
            ? `
            <button
              class="btn green"
              onclick="updateApplication('${item.id}','accepted')">
              ✓ Accept
            </button>
            `
            : ""
          }

          ${
            status !== "rejected"
            ? `
            <button
              class="btn red"
              onclick="updateApplication('${item.id}','rejected')">
              ✕ Reject
            </button>
            `
            : ""
          }

          <button
            class="btn secondary"
            onclick="deleteApplication('${item.id}')">
            Delete
          </button>

        </div>

      </div>

      `;

    }).join("");

  })
  .catch(error=>{

    console.error(error);

    document.getElementById("applicationsList").innerHTML = `
      <div class="card">
        Applications load नहीं हो सकीं।
      </div>
    `;

  });

}


function updateApplication(id,status){

  if(!isAdmin){
    return;
  }

  db.ref("applications/"+id)
    .update({
      status:status,
      updatedAt:Date.now()
    })
    .then(()=>{

      showToast(
        status === "accepted"
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

  if(!isAdmin){
    return;
  }

  if(!confirm("क्या आप यह application delete करना चाहते हैं?")){
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


/* =====================================================
   NEWS ADMIN
===================================================== */

document.getElementById("newsForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  if(!isAdmin){
    return;
  }

  const id =
    document.getElementById("editNewsId").value;

  const data = {

    title:
      document.getElementById("newsTitle").value.trim(),

    details:
      document.getElementById("newsDetails").value.trim(),

    date:now(),

    updatedAt:Date.now()

  };

  try{

    if(id){

      await db.ref("news/"+id).update(data);

      showToast("News updated");

    }else{

      data.createdAt=Date.now();

      await db.ref("news").push(data);

      showToast("News added");

    }

    clearNewsForm();

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

  if(!isAdmin){
    return;
  }

  db.ref("news").once("value")
  .then(snapshot=>{

    const data=snapshot.val() || {};

    const list=
      Object.entries(data)
      .map(([id,item])=>({
        id,
        ...item
      }))
      .sort((a,b)=>
        (b.createdAt || 0) -
        (a.createdAt || 0)
      );

    const box =
      document.getElementById("adminNewsList");

    if(!list.length){

      box.innerHTML=`
        <p class="help">
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

        <p class="help">
          ${escapeHTML(item.date || "")}
        </p>

        <p style="margin-top:8px;white-space:pre-wrap">
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

      if(!item){
        return;
      }

      document.getElementById("editNewsId").value=id;

      document.getElementById("newsTitle").value=
        item.title || "";

      document.getElementById("newsDetails").value=
        item.details || "";

      document
        .getElementById("newsTitle")
        .scrollIntoView({
          behavior:"smooth",
          block:"center"
        });

    });

}


function deleteNews(id){

  if(!isAdmin){
    return;
  }

  if(!confirm("क्या आप यह news delete करना चाहते हैं?")){
    return;
  }

  db.ref("news/"+id)
    .remove()
    .then(()=>{

      showToast("News deleted");

      renderAdminNews();

    })
    .catch(error=>{

      console.error(error);

      showToast("News delete नहीं हुई।");

    });

}


/* =====================================================
   GALLERY
===================================================== */

/*
  यहाँ default gallery में custom temple-style
  illustration दिखाई जाएगी।

  बाद में Admin Panel से अपनी फोटो का direct
  image URL add किया जा सकता है।
*/

const defaultGallery = [

  {
    type:"illustration",
    caption:"श्री राम जानकी मंदिर"
  },

  {
    type:"illustration",
    caption:"मंदिर सेवा एवं धार्मिक आयोजन"
  },

  {
    type:"illustration",
    caption:"दुर्गा पूजा सेवा समिति"
  }

];


function templeIllustration(){

  return `

    <div class="templeCard">

      <div class="miniTemple"></div>

    </div>

  `;

}


function loadGallery(){

  db.ref("gallery").on("value",snapshot=>{

    const data=snapshot.val() || {};

    const custom =
      Object.entries(data)
      .map(([id,item])=>({
        id,
        ...item
      }))
      .sort((a,b)=>
        (b.createdAt || 0) -
        (a.createdAt || 0)
      );

    const box =
      document.getElementById("galleryGrid");

    let html="";

    defaultGallery.forEach(item=>{

      html += `

        <div class="galleryItem">

          ${templeIllustration()}

          <div class="galleryCaption">
            ${escapeHTML(item.caption)}
          </div>

        </div>

      `;

    });

    custom.forEach(item=>{

      const url=safeURL(item.url);

      if(!url){
        return;
      }

      html += `

        <div class="galleryItem">

          <img
            src="${url}"
            alt="${escapeHTML(item.caption || "मंदिर फोटो")}"
            loading="lazy"
            onerror="this.style.display='none'">

          <div class="galleryCaption">

            ${escapeHTML(
              item.caption || "मंदिर फोटो"
            )}

            ${
              isAdmin
              ? `
              <div style="margin-top:8px">

                <button
                  class="btn red"
                  onclick="deleteGallery('${item.id}')">
                  Delete
                </button>

              </div>
              `
              : ""
            }

          </div>

        </div>

      `;

    });

    box.innerHTML=html;

  });

}


document.getElementById("galleryForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  if(!isAdmin){
    return;
  }

  const url =
    safeURL(
      document.getElementById("galleryUrl")
      .value.trim()
    );

  if(!url){

    showToast("Valid image URL डालें।");

    return;
  }

  const caption =
    document.getElementById("galleryCaption")
    .value.trim();

  try{

    await db.ref("gallery").push({

      url:url,

      caption:caption || "मंदिर फोटो",

      createdAt:Date.now()

    });

    document.getElementById("galleryUrl").value="";

    document.getElementById("galleryCaption").value="";

    showToast("Gallery में photo add हो गई।");

  }catch(error){

    console.error(error);

    showToast("Photo add नहीं हुई।");

  }

});


function deleteGallery(id){

  if(!isAdmin){
    return;
  }

  if(!confirm("क्या आप यह photo delete करना चाहते हैं?")){
    return;
  }

  db.ref("gallery/"+id)
    .remove()
    .then(()=>{

      showToast("Photo deleted");

    })
    .catch(error=>{

      console.error(error);

      showToast("Photo delete नहीं हुई।");

    });

}


/* =====================================================
   INITIAL LOAD
===================================================== */

loadNews();

loadGallery();

</script>

</body>
</html>
