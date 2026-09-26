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
  background:#fffaf2;
  color:#32170d;
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

/* ================= HEADER ================= */

.hero{
  min-height:470px;
  position:relative;
  overflow:hidden;
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  text-align:center;
  padding:45px 18px;
  background:
    radial-gradient(circle at 50% 18%,rgba(255,226,133,.35),transparent 23%),
    linear-gradient(135deg,#5d120b,#a9270e 48%,#e87516);
}

.hero:before{
  content:"";
  position:absolute;
  width:420px;
  height:420px;
  border-radius:50%;
  background:rgba(255,255,255,.06);
  left:-170px;
  bottom:-220px;
}

.hero:after{
  content:"";
  position:absolute;
  width:350px;
  height:350px;
  border-radius:50%;
  background:rgba(255,255,255,.06);
  right:-150px;
  top:-190px;
}

.heroContent{
  position:relative;
  z-index:2;
  max-width:900px;
  width:100%;
}

.om{
  font-size:48px;
  margin-bottom:8px;
}

.templeLogo{
  width:210px;
  height:145px;
  position:relative;
  margin:5px auto 20px;
}

.templeBody{
  position:absolute;
  left:37px;
  right:37px;
  bottom:8px;
  height:80px;
  background:#fff1c9;
  border:4px solid #e4a128;
}

.templeDoor{
  position:absolute;
  bottom:8px;
  left:82px;
  width:46px;
  height:64px;
  border-radius:25px 25px 0 0;
  background:#6e160d;
  border:3px solid #dfa027;
}

.templeRoof{
  position:absolute;
  top:35px;
  left:25px;
  right:25px;
  height:55px;
  background:#ffd66f;
  clip-path:polygon(50% 0,100% 100%,0 100%);
}

.templeRoof2{
  position:absolute;
  top:57px;
  left:47px;
  right:47px;
  height:45px;
  background:#ffe6a2;
  clip-path:polygon(50% 0,100% 100%,0 100%);
}

.templeFlagPole{
  position:absolute;
  top:0;
  left:103px;
  width:5px;
  height:48px;
  background:#f8d17a;
}

.templeFlag{
  position:absolute;
  top:3px;
  left:107px;
  width:42px;
  height:23px;
  background:#ef3d17;
  clip-path:polygon(0 0,100% 25%,72% 50%,100% 75%,0 100%);
}

.hero h1{
  font-size:clamp(28px,6vw,48px);
  line-height:1.2;
  text-shadow:0 3px 10px rgba(0,0,0,.3);
}

.heroSub{
  margin-top:10px;
  font-size:18px;
  opacity:.96;
}

.location{
  margin-top:5px;
  font-size:15px;
  opacity:.9;
}

.jai{
  display:inline-block;
  margin-top:17px;
  padding:8px 22px;
  border:1px solid rgba(255,255,255,.5);
  border-radius:30px;
  background:rgba(255,255,255,.12);
  font-weight:bold;
}

/* ================= NAV ================= */

nav{
  position:sticky;
  top:0;
  z-index:100;
  background:#481009;
  box-shadow:0 3px 15px rgba(0,0,0,.2);
}

.navInner{
  max-width:1150px;
  margin:auto;
  padding:8px 12px;
  display:flex;
  justify-content:center;
  gap:5px;
  overflow-x:auto;
}

nav a{
  color:#fff;
  white-space:nowrap;
  padding:9px 14px;
  border-radius:22px;
  font-size:14px;
  transition:.2s;
}

nav a:hover{
  background:#c65b14;
}

/* ================= COMMON ================= */

.container{
  max-width:1120px;
  margin:auto;
  padding:60px 16px;
}

.sectionHead{
  text-align:center;
  margin-bottom:30px;
}

.sectionHead .smallTitle{
  color:#c45a13;
  font-size:13px;
  font-weight:bold;
  letter-spacing:1px;
  text-transform:uppercase;
}

.sectionHead h2{
  color:#7e200e;
  font-size:30px;
  margin-top:4px;
}

.sectionHead p{
  color:#766258;
  margin-top:5px;
}

.card{
  background:#fff;
  border:1px solid #f0dfcc;
  border-radius:18px;
  box-shadow:0 6px 25px rgba(74,31,9,.08);
  padding:24px;
}

.grid{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:20px;
}

/* ================= WELCOME ================= */

.welcome{
  text-align:center;
  max-width:850px;
  margin:auto;
}

.welcomeBadge{
  display:inline-block;
  padding:6px 14px;
  border-radius:20px;
  background:#fff1dc;
  color:#a64210;
  font-size:13px;
  font-weight:bold;
  margin-bottom:12px;
}

.welcome h2{
  color:#7e200e;
  font-size:28px;
  margin-bottom:10px;
}

.welcome p{
  color:#604b40;
}

.feature{
  text-align:center;
}

.featureIcon{
  font-size:37px;
  margin-bottom:8px;
}

.feature h3{
  color:#7e200e;
  margin-bottom:5px;
}

.feature p{
  color:#735f55;
  font-size:14px;
}

/* ================= NEWS ================= */

.newsGrid{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:18px;
}

.newsCard{
  border-left:5px solid #d86c18;
}

.newsDate{
  font-size:12px;
  color:#9a7867;
  margin-bottom:5px;
}

.newsTitle{
  color:#81200d;
  font-size:21px;
  font-weight:bold;
  margin-bottom:7px;
}

.newsText{
  color:#59463d;
  white-space:pre-wrap;
}

.readTag{
  display:inline-block;
  margin-top:12px;
  color:#b34c10;
  font-size:13px;
  font-weight:bold;
}

/* ================= GALLERY ================= */

.galleryGrid{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:18px;
}

.galleryItem{
  background:#fff;
  border-radius:16px;
  overflow:hidden;
  border:1px solid #eedcc8;
  box-shadow:0 5px 20px rgba(60,25,8,.09);
}

.galleryItem img{
  display:block;
  width:100%;
  height:220px;
  object-fit:cover;
}

.galleryCaption{
  padding:12px;
  text-align:center;
  font-weight:bold;
  color:#71301d;
}

.templeIllustration{
  height:220px;
  position:relative;
  overflow:hidden;
  background:
    radial-gradient(circle at 50% 30%,#fff1a9 0 7%,transparent 8%),
    linear-gradient(#e9781b,#9c1d0d);
}

.miniTemple{
  position:absolute;
  left:15%;
  right:15%;
  bottom:20px;
  height:120px;
  background:#fff0c7;
  border:5px solid #e0a027;
}

.miniTemple:before{
  content:"";
  position:absolute;
  left:5%;
  right:5%;
  top:-55px;
  height:60px;
  background:#ffd66d;
  clip-path:polygon(50% 0,100% 100%,0 100%);
}

.miniTemple:after{
  content:"";
  position:absolute;
  left:41%;
  bottom:0;
  width:18%;
  height:70px;
  background:#74160c;
  border-radius:30px 30px 0 0;
}

/* ================= FORM ================= */

.formGrid{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:16px;
}

.field{
  display:flex;
  flex-direction:column;
  gap:6px;
}

.full{
  grid-column:1/-1;
}

label{
  color:#502619;
  font-weight:bold;
  font-size:14px;
}

input,
textarea,
select{
  width:100%;
  padding:12px 13px;
  border:1px solid #dec8b2;
  border-radius:10px;
  background:#fffdfa;
  color:#352016;
  outline:none;
}

input:focus,
textarea:focus,
select:focus{
  border-color:#c85e15;
  box-shadow:0 0 0 3px rgba(200,94,21,.09);
}

textarea{
  min-height:110px;
  resize:vertical;
}

.supportBox{
  background:#fff7e8;
  border:1px solid #f0d6ac;
  border-radius:12px;
  padding:14px;
}

.help{
  font-size:12px;
  color:#806b60;
}

.formActions{
  text-align:center;
  margin-top:20px;
}

.btn{
  border:0;
  border-radius:10px;
  padding:11px 18px;
  color:#fff;
  background:linear-gradient(135deg,#9d270f,#d96816);
  font-weight:bold;
  transition:.2s;
}

.btn:hover{
  transform:translateY(-1px);
  box-shadow:0 5px 14px rgba(120,45,10,.2);
}

.btn.green{
  background:#23843a;
}

.btn.red{
  background:#bd2929;
}

.btn.gray{
  background:#555;
}

/* ================= ADMIN ================= */

.adminLogin{
  max-width:430px;
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
  margin-bottom:20px;
}

.adminHeader h3{
  color:#7d200d;
}

.filters{
  display:flex;
  gap:10px;
  margin:15px 0;
  flex-wrap:wrap;
}

.filters input{
  flex:1;
  min-width:220px;
}

.application{
  background:#fffdfa;
  border:1px solid #ead9c8;
  border-radius:14px;
  padding:17px;
  margin-top:14px;
}

.appTop{
  display:flex;
  justify-content:space-between;
  gap:12px;
  flex-wrap:wrap;
  padding-bottom:10px;
  border-bottom:1px solid #eadfd5;
}

.appTop h3{
  color:#74200f;
}

.status{
  display:inline-block;
  padding:4px 11px;
  border-radius:20px;
  font-size:11px;
  font-weight:bold;
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
  gap:8px 20px;
  margin-top:12px;
  font-size:14px;
}

.appInfo b{
  color:#66301d;
}

.appButtons{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  margin-top:15px;
}

/* ================= FOOTER ================= */

footer{
  background:#390d08;
  color:#f9d9ae;
  text-align:center;
  padding:32px 15px;
}

footer strong{
  color:#fff;
}

/* ================= TOAST ================= */

#toast{
  position:fixed;
  z-index:500;
  left:50%;
  bottom:25px;
  transform:translate(-50%,120px);
  opacity:0;
  background:#30120b;
  color:#fff;
  padding:12px 20px;
  border-radius:30px;
  transition:.3s;
  max-width:90%;
  text-align:center;
}

#toast.show{
  opacity:1;
  transform:translate(-50%,0);
}

/* ================= MOBILE ================= */

@media(max-width:850px){

  .grid,
  .galleryGrid{
    grid-template-columns:repeat(2,1fr);
  }

}

@media(max-width:650px){

  .hero{
    min-height:430px;
  }

  .grid,
  .galleryGrid,
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
    padding:45px 13px;
  }

  .sectionHead h2{
    font-size:26px;
  }

  .hero h1{
    font-size:29px;
  }

  nav a{
    padding:8px 11px;
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
    <a href="#gallery">Gallery</a>
    <a href="#volunteer">Volunteer</a>
    <a href="#committee">Committee</a>
    <a href="#admin">Admin Panel</a>

  </div>

</nav>

<!-- ================= WELCOME ================= -->

<section class="container">

  <div class="card welcome">

    <div class="welcomeBadge">
      WELCOME
    </div>

    <h2>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h2>

    <p>
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति की
      official website पर आपका हार्दिक स्वागत है।
    </p>

    <p style="margin-top:8px">
      धार्मिक सेवा, सामाजिक सहयोग और मंदिर से संबंधित
      latest updates यहाँ प्राप्त करें।
    </p>

  </div>

  <div class="grid" style="margin-top:22px">

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

<!-- ================= GALLERY ================= -->

<section id="gallery" class="container">

  <div class="sectionHead">

    <div class="smallTitle">
      Photo Gallery
    </div>

    <h2>🖼️ मंदिर गैलरी</h2>

    <p>
      मंदिर एवं समिति की झलकियाँ
    </p>

  </div>

  <div id="galleryGrid" class="galleryGrid"></div>

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
      Applications, News और Gallery manage करें।
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
            Manage Applications • News • Gallery
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

    <div class="card" style="margin-top:20px">

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

    <div class="card" style="margin-top:20px">

      <h3>📰 Manage News</h3>

      <form id="newsForm" style="margin-top:16px">

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

    <!-- GALLERY MANAGEMENT -->

    <div class="card" style="margin-top:20px">

      <h3>🖼️ Manage Gallery</h3>

      <form id="galleryForm" style="margin-top:16px">

        <div class="formGrid">

          <div class="field">

            <label>Image URL</label>

            <input
              id="galleryUrl"
              type="url"
              required
              placeholder="https://...">

          </div>

          <div class="field">

            <label>Caption</label>

            <input
              id="galleryCaption"
              maxlength="100"
              placeholder="Photo caption">

          </div>

        </div>

        <div class="formActions">

          <button class="btn" type="submit">
            Add to Gallery
          </button>

        </div>

      </form>

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

  <p style="margin-top:8px">
    जय श्री राम 🚩
  </p>

  <p style="font-size:12px;margin-top:10px;opacity:.7">
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

    loadGallery();

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
              <div style="margin-top:12px">
                <b>Message:</b><br>
                ${escapeHTML(item.message)}
              </div>
              `
              :""
            }

            ${
              photo
              ? `
              <div style="margin-top:10px">
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
              <div style="margin-top:7px">
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

  const data={

    title:
      document.getElementById("newsTitle")
      .value.trim(),

    details:
      document.getElementById("newsDetails")
      .value.trim(),

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
          <p class="help" style="margin-top:20px">
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
            margin-top:8px;
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

    });

}


/* ================= GALLERY ================= */

const defaultGallery=[
  "श्री राम जानकी मंदिर",
  "मंदिर सेवा",
  "दुर्गा पूजा सेवा समिति"
];


function templeImage(){

  return`
    <div class="templeIllustration">
      <div class="miniTemple"></div>
    </div>
  `;

}


function loadGallery(){

  db.ref("gallery")
    .on("value",snapshot=>{

      const data=snapshot.val() || {};

      const custom=
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
          "galleryGrid"
        );

      let html="";

      defaultGallery.forEach(caption=>{

        html+=`

          <div class="galleryItem">

            ${templeImage()}

            <div class="galleryCaption">
              ${escapeHTML(caption)}
            </div>

          </div>

        `;

      });

      custom.forEach(item=>{

        const url=safeURL(item.url);

        if(!url)return;

        html+=`

          <div class="galleryItem">

            <img
              src="${url}"
              alt="${escapeHTML(
                item.caption||"Temple Photo"
              )}"
              loading="lazy">

            <div class="galleryCaption">

              ${escapeHTML(
                item.caption||"Temple Photo"
              )}

              ${
                isAdmin
                ? `
                <div style="margin-top:8px">

                  <button
                    class="btn red"
                    onclick="deleteGallery(
                      '${item.id}'
                    )">
                    Delete
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

    });

}


document
.getElementById("galleryForm")
.addEventListener("submit",async function(e){

  e.preventDefault();

  if(!isAdmin)return;

  const url=
    safeURL(
      document.getElementById(
        "galleryUrl"
      ).value.trim()
    );

  if(!url){

    showToast("Valid image URL डालें।");

    return;
  }

  const caption=
    document.getElementById(
      "galleryCaption"
    ).value.trim();

  try{

    await db.ref("gallery").push({

      url,

      caption:
        caption||"Temple Photo",

      createdAt:Date.now()

    });

    document.getElementById(
      "galleryUrl"
    ).value="";

    document.getElementById(
      "galleryCaption"
    ).value="";

    showToast(
      "Photo added to Gallery!"
    );

  }catch(error){

    console.error(error);

    showToast(
      "Photo add नहीं हुई।"
    );

  }

});


function deleteGallery(id){

  if(!confirm(
    "क्या आप यह photo delete करना चाहते हैं?"
  )){
    return;
  }

  db.ref("gallery/"+id)
    .remove()
    .then(()=>{

      showToast("Photo deleted!");

    });

}


/* ================= START ================= */

loadNews();

loadGallery();

</script>

</body>
</html>
