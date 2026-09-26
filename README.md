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

body{
  margin:0;
  font-family:Arial,sans-serif;
  background:#fff8ed;
  color:#222;
}

header{
  background:linear-gradient(135deg,#8b0000,#d35400,#ff9800);
  color:#fff;
  text-align:center;
  padding:25px 15px;
}

header h1{
  margin:0;
  font-size:25px;
}

header p{
  margin:7px 0;
}

nav{
  position:sticky;
  top:0;
  z-index:20;
  display:flex;
  flex-wrap:wrap;
  justify-content:center;
  gap:7px;
  padding:10px;
  background:#fff;
  box-shadow:0 2px 8px #bbb;
}

nav button{
  border:0;
  background:#8b0000;
  color:#fff;
  padding:10px 14px;
  border-radius:20px;
  cursor:pointer;
}

section{
  max-width:1050px;
  margin:auto;
  padding:25px 15px;
}

.card{
  background:#fff;
  border-radius:15px;
  padding:18px;
  margin:15px 0;
  box-shadow:0 3px 12px #ddd;
}

h2{
  color:#8b0000;
}

input,textarea,select{
  width:100%;
  padding:12px;
  margin:7px 0 12px;
  border:1px solid #ccc;
  border-radius:9px;
  font-size:15px;
}

textarea{
  min-height:100px;
}

button.main{
  border:0;
  padding:11px 17px;
  border-radius:8px;
  background:#8b0000;
  color:#fff;
  cursor:pointer;
  font-weight:bold;
}

button.green{background:#16803c}
button.red{background:#b00020}
button.orange{background:#e87500}
button.gray{background:#555}

button:disabled{
  opacity:.6;
}

.small{
  color:#666;
  font-size:13px;
}

.actions{
  display:flex;
  flex-wrap:wrap;
  gap:7px;
  margin-top:12px;
}

.actions button{
  border:0;
  color:#fff;
  padding:8px 11px;
  border-radius:7px;
  cursor:pointer;
}

.news{
  border-left:5px solid #d35400;
}

.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
  gap:15px;
}

.galleryItem{
  background:#fff;
  border-radius:12px;
  padding:10px;
  box-shadow:0 2px 8px #ddd;
}

.galleryItem img{
  width:100%;
  height:190px;
  object-fit:cover;
  border-radius:9px;
}

.status{
  display:inline-block;
  padding:5px 10px;
  border-radius:15px;
  font-size:12px;
  font-weight:bold;
}

.pending{
  background:#fff0b3;
}

.accepted{
  background:#b9f6ca;
}

.rejected{
  background:#ffcdd2;
}

.adminPanel{
  display:none;
}

.modal{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.75);
  z-index:100;
  overflow:auto;
  padding:20px;
}

.modalBox{
  background:#fff;
  max-width:700px;
  margin:30px auto;
  padding:20px;
  border-radius:15px;
}

footer{
  background:#5b0000;
  color:#fff;
  text-align:center;
  padding:25px;
  margin-top:30px;
}

.loading{
  text-align:center;
  padding:20px;
  color:#777;
}

@media(max-width:500px){
  header h1{
    font-size:21px;
  }

  nav button{
    padding:8px 11px;
    font-size:13px;
  }
}
</style>
</head>

<body>

<header>
  <h1>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</h1>
  <p>Siswa Bazar</p>
  <h3>जय श्री राम 🚩</h3>
</header>

<nav>
  <button onclick="goTo('home')">Home</button>
  <button onclick="goTo('news')">News</button>
  <button onclick="goTo('gallery')">Gallery</button>
  <button onclick="goTo('volunteer')">Volunteer</button>
  <button onclick="goTo('committee')">Committee</button>
  <button onclick="goTo('admin')">Admin</button>
</nav>


<!-- HOME -->

<section id="home">

  <div class="card" style="text-align:center">

    <h2>🙏 स्वागत है 🙏</h2>

    <p>
      श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति,
      Siswa Bazar की आधिकारिक वेबसाइट पर
      आपका हार्दिक स्वागत है।
    </p>

    <h3>जय श्री राम 🚩</h3>

  </div>

</section>


<!-- NEWS -->

<section id="news">

  <h2>📰 News & Updates</h2>

  <div id="newsList">
    <div class="loading">
      News loading...
    </div>
  </div>

</section>


<!-- GALLERY -->

<section id="gallery">

  <h2>🖼️ Gallery</h2>

  <div class="card">

    <div id="galleryList" class="gallery">
      <div class="loading">
        Gallery loading...
      </div>
    </div>

  </div>

</section>


<!-- VOLUNTEER -->

<section id="volunteer">

  <h2>🙋 Volunteer Application</h2>

  <div class="card">

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
        placeholder="10 digit Mobile Number"
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

      <label>
        <b>📷 Photo Upload</b>
      </label>

      <input
        id="vPhoto"
        type="file"
        accept="image/*"
        required>

      <label>
        <b>📄 Application PDF</b>
      </label>

      <input
        id="vPdf"
        type="file"
        accept="application/pdf"
        required>

      <textarea
        id="vMessage"
        placeholder="अन्य जानकारी / संदेश"></textarea>

      <button
        class="main"
        type="submit">
        Submit Application
      </button>

      <p id="vStatus" class="small"></p>

    </form>

  </div>

</section>


<!-- COMMITTEE -->

<section id="committee">

  <h2>👥 Committee Member Application</h2>

  <div class="card">

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
        placeholder="10 digit Mobile Number"
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

      <label>
        <b>📷 Photo Upload</b>
      </label>

      <input
        id="cPhoto"
        type="file"
        accept="image/*"
        required>

      <textarea
        id="cMessage"
        placeholder="अन्य जानकारी / संदेश"></textarea>

      <button
        class="main"
        type="submit">
        Submit Committee Application
      </button>

      <p id="cStatus" class="small"></p>

    </form>

  </div>

</section>


<!-- ADMIN -->

<section id="admin">

  <h2>🔐 Admin Panel</h2>

  <div class="card" id="loginBox">

    <input
      id="adminPassword"
      type="password"
      placeholder="Admin Password">

    <button
      class="main"
      onclick="adminLogin()">
      Login
    </button>

    <p id="loginStatus" class="small"></p>

  </div>


  <div
    id="adminPanel"
    class="adminPanel">

    <!-- APPLICATIONS -->

    <div class="card">

      <h3>📋 Applications</h3>

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
        placeholder="Search name or mobile">

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
        Add News
      </button>

    </div>


    <!-- GALLERY ADMIN -->

    <div class="card">

      <h3>🖼️ Add Gallery Photo</h3>

      <input
        id="galleryTitle"
        placeholder="Photo Title">

      <input
        id="galleryFile"
        type="file"
        accept="image/*">

      <button
        class="main"
        onclick="uploadGallery()">
        Upload Photo
      </button>

      <p
        id="galleryStatus"
        class="small"></p>

    </div>


    <button
      class="main red"
      onclick="adminLogout()">
      Logout
    </button>

  </div>

</section>


<!-- NEWS READER -->

<div
  class="modal"
  id="newsModal">

  <div class="modalBox">

    <h2 id="modalTitle"></h2>

    <p id="modalDetails"></p>

    <button
      class="main"
      onclick="closeNews()">
      Close
    </button>

  </div>

</div>


<footer>

  <b>
    श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति
  </b>

  <br>

  Siswa Bazar

  <br><br>

  जय श्री राम 🚩

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

const db = firebase.database();


/* =========================================================
   CLOUDINARY
   BAS YE 2 VALUES BAAD MEIN LAGENGI
========================================================= */

const CLOUDINARY_CLOUD_NAME =
  "YOUR_CLOUD_NAME";

const CLOUDINARY_UPLOAD_PRESET =
  "YOUR_UPLOAD_PRESET";


/* =========================================================
   ADMIN
========================================================= */

const ADMIN_PASSWORD =
  "SRJM2026";

let isAdmin = false;

let applications = {};
let newsData = {};
let galleryData = {};


/* =========================================================
   NAVIGATION
========================================================= */

function goTo(id){

  document.getElementById(id)
    .scrollIntoView({
      behavior:"smooth"
    });

}


/* =========================================================
   CLOUDINARY UPLOAD
========================================================= */

async function uploadToCloudinary(file,type){

  if(!file){

    throw new Error(
      "File select nahi ki gayi."
    );

  }


  if(
    CLOUDINARY_CLOUD_NAME === "YOUR_CLOUD_NAME" ||
    CLOUDINARY_UPLOAD_PRESET === "YOUR_UPLOAD_PRESET"
  ){

    throw new Error(
      "Cloudinary setup abhi complete nahi hai."
    );

  }


  const formData =
    new FormData();

  formData.append(
    "file",
    file
  );

  formData.append(
    "upload_preset",
    CLOUDINARY_UPLOAD_PRESET
  );


  const resourceType =
    type === "pdf"
    ? "raw"
    : "image";


  const uploadURL =
    "https://api.cloudinary.com/v1_1/" +
    CLOUDINARY_CLOUD_NAME +
    "/" +
    resourceType +
    "/upload";


  const response =
    await fetch(
      uploadURL,
      {
        method:"POST",
        body:formData
      }
    );


  const data =
    await response.json();


  if(!response.ok){

    throw new Error(
      data.error?.message ||
      "Upload failed."
    );

  }


  return data.secure_url;

}


/* =========================================================
   VOLUNTEER
========================================================= */

document
  .getElementById("volunteerForm")
  .addEventListener(
    "submit",
    async function(e){

      e.preventDefault();

      const status =
        document.getElementById(
          "vStatus"
        );


      const mobile =
        document.getElementById(
          "vMobile"
        ).value.trim();


      if(!/^[0-9]{10}$/.test(mobile)){

        status.innerText =
          "❌ Mobile number 10 digit ka hona chahiye.";

        return;

      }


      try{

        status.innerText =
          "⏳ Photo upload ho rahi hai...";


        const photoURL =
          await uploadToCloudinary(
            document.getElementById(
              "vPhoto"
            ).files[0],
            "image"
          );


        status.innerText =
          "⏳ PDF upload ho rahi hai...";


        const pdfURL =
          await uploadToCloudinary(
            document.getElementById(
              "vPdf"
            ).files[0],
            "pdf"
          );


        status.innerText =
          "⏳ Application save ho rahi hai...";


        const ref =
          db.ref(
            "applications"
          ).push();


        await ref.set({

          type:"volunteer",

          name:
            document.getElementById(
              "vName"
            ).value.trim(),

          mobile:mobile,

          age:
            document.getElementById(
              "vAge"
            ).value,

          address:
            document.getElementById(
              "vAddress"
            ).value.trim(),

          contribution:
            document.getElementById(
              "vContribution"
            ).value.trim(),

          message:
            document.getElementById(
              "vMessage"
            ).value.trim(),

          photo:photoURL,

          pdfLink:pdfURL,

          status:"pending",

          createdAt:
            firebase.database
              .ServerValue
              .TIMESTAMP

        });


        document
          .getElementById(
            "volunteerForm"
          )
          .reset();


        status.innerText =
          "✅ Volunteer application successfully submit ho gayi.";

      }
      catch(error){

        console.error(error);

        status.innerText =
          "❌ " +
          error.message;

      }

    }
  );


/* =========================================================
   COMMITTEE
========================================================= */

document
  .getElementById("committeeForm")
  .addEventListener(
    "submit",
    async function(e){

      e.preventDefault();

      const status =
        document.getElementById(
          "cStatus"
        );


      const mobile =
        document.getElementById(
          "cMobile"
        ).value.trim();


      if(!/^[0-9]{10}$/.test(mobile)){

        status.innerText =
          "❌ Mobile number 10 digit ka hona chahiye.";

        return;

      }


      try{

        status.innerText =
          "⏳ Photo upload ho rahi hai...";


        const photoURL =
          await uploadToCloudinary(
            document.getElementById(
              "cPhoto"
            ).files[0],
            "image"
          );


        status.innerText =
          "⏳ Application save ho rahi hai...";


        const ref =
          db.ref(
            "applications"
          ).push();


        await ref.set({

          type:"committee",

          name:
            document.getElementById(
              "cName"
            ).value.trim(),

          mobile:mobile,

          age:
            document.getElementById(
              "cAge"
            ).value,

          address:
            document.getElementById(
              "cAddress"
            ).value.trim(),

          contribution:
            document.getElementById(
              "cContribution"
            ).value.trim(),

          message:
            document.getElementById(
              "cMessage"
            ).value.trim(),

          photo:photoURL,

          pdfLink:"",

          status:"pending",

          createdAt:
            firebase.database
              .ServerValue
              .TIMESTAMP

        });


        document
          .getElementById(
            "committeeForm"
          )
          .reset();


        status.innerText =
          "✅ Committee application successfully submit ho gayi.";

      }
      catch(error){

        console.error(error);

        status.innerText =
          "❌ " +
          error.message;

      }

    }
  );


/* =========================================================
   LOAD APPLICATIONS
========================================================= */

db.ref("applications")
.on(
  "value",
  snapshot=>{

    applications =
      snapshot.val() || {};

    if(isAdmin){

      renderApplications();

    }

  }
);


/* =========================================================
   ADMIN LOGIN
========================================================= */

function adminLogin(){

  const password =
    document.getElementById(
      "adminPassword"
    ).value;


  if(password === ADMIN_PASSWORD){

    isAdmin = true;


    document.getElementById(
      "loginBox"
    ).style.display =
      "none";


    document.getElementById(
      "adminPanel"
    ).style.display =
      "block";


    renderApplications();

    renderNews();

    renderGallery();

  }
  else{

    document.getElementById(
      "loginStatus"
    ).innerText =
      "❌ Wrong password.";

  }

}


function adminLogout(){

  isAdmin = false;


  document.getElementById(
    "loginBox"
  ).style.display =
    "block";


  document.getElementById(
    "adminPanel"
  ).style.display =
    "none";


  document.getElementById(
    "adminPassword"
  ).value = "";

}


/* =========================================================
   APPLICATION LIST
========================================================= */

function renderApplications(){

  const box =
    document.getElementById(
      "applicationsList"
    );


  if(!box)return;


  const filter =
    document.getElementById(
      "statusFilter"
    ).value;


  const search =
    document.getElementById(
      "applicationSearch"
    ).value
    .toLowerCase()
    .trim();


  let html = "";


  Object.entries(applications)
    .reverse()
    .forEach(
      ([key,item])=>{

        const name =
          String(
            item.name || ""
          );


        const mobile =
          String(
            item.mobile || ""
          );


        const status =
          item.status ||
          "pending";


        if(
          filter !== "all" &&
          status !== filter
        ){

          return;

        }


        if(
          search &&
          !name
            .toLowerCase()
            .includes(search) &&
          !mobile.includes(search)
        ){

          return;

        }


        const type =
          item.type === "committee"
          ? "Committee Member"
          : "Volunteer";


        html += `

          <div class="card">

            <h3>
              ${escapeHTML(name)}
            </h3>

            <p>
              <b>Type:</b>
              ${type}
            </p>

            <p>
              <b>Mobile:</b>
              ${escapeHTML(mobile)}
            </p>

            <p>
              <b>Age:</b>
              ${escapeHTML(item.age || "")}
            </p>

            <p>
              <b>Address:</b>
              ${escapeHTML(item.address || "")}
            </p>

            <p>
              <b>Contribution:</b>
              ${escapeHTML(item.contribution || "")}
            </p>

            <p>
              <b>Message:</b>
              ${escapeHTML(item.message || "")}
            </p>

            <span class="status ${status}">
              ${status.toUpperCase()}
            </span>

            ${
              item.photo
              ?
              `
              <p>
                <a
                  href="${item.photo}"
                  target="_blank">
                  📷 View Photo
                </a>
              </p>
              `
              : ""
            }

            ${
              item.pdfLink
              ?
              `
              <p>
                <a
                  href="${item.pdfLink}"
                  target="_blank">
                  📄 View Application PDF
                </a>
              </p>
              `
              : ""
            }

            <div class="actions">

              <button
                class="green"
                onclick="changeStatus('${key}','accepted')">
                Accept
              </button>

              <button
                class="red"
                onclick="changeStatus('${key}','rejected')">
                Reject
              </button>

              <button
                class="gray"
                onclick="deleteApplication('${key}')">
                Delete
              </button>

            </div>

          </div>

        `;

      }
    );


  if(!html){

    html =
      `
      <div class="card">
        No applications found.
      </div>
      `;

  }


  box.innerHTML =
    html;

}


/* =========================================================
   CHANGE STATUS
========================================================= */

function changeStatus(
  key,
  status
){

  if(!isAdmin)return;


  db.ref(
    "applications/" +
    key
  )
  .update({
    status:status
  });

}


/* =========================================================
   DELETE APPLICATION
========================================================= */

function deleteApplication(key){

  if(!isAdmin)return;


  if(
    !confirm(
      "Kya aap is application ko delete karna chahte hain?"
    )
  ){

    return;

  }


  db.ref(
    "applications/" +
    key
  ).remove();

}


/* =========================================================
   NEWS LOAD
========================================================= */

db.ref("news")
.on(
  "value",
  snapshot=>{

    newsData =
      snapshot.val() || {};

    renderNews();

  }
);


/* =========================================================
   ADD NEWS
========================================================= */

function addNews(){

  if(!isAdmin)return;


  const title =
    document.getElementById(
      "newsTitle"
    ).value.trim();


  const details =
    document.getElementById(
      "newsDetails"
    ).value.trim();


  if(!title || !details){

    alert(
      "News title aur details bharein."
    );

    return;

  }


  db.ref("news")
    .push({

      title:title,

      details:details,

      createdAt:
        firebase.database
          .ServerValue
          .TIMESTAMP

    });


  document.getElementById(
    "newsTitle"
  ).value = "";


  document.getElementById(
    "newsDetails"
  ).value = "";


  alert(
    "✅ News added successfully."
  );

}


/* =========================================================
   RENDER NEWS
========================================================= */

function renderNews(){

  const box =
    document.getElementById(
      "newsList"
    );


  if(!box)return;


  let html = "";


  const list =
    Object.entries(newsData)
      .sort(
        (a,b)=>
          (b[1].createdAt || 0) -
          (a[1].createdAt || 0)
      );


  list.forEach(
    ([key,item])=>{

      html += `

        <div class="card news">

          <h3>
            ${escapeHTML(
              item.title || ""
            )}
          </h3>

          <p>
            ${escapeHTML(
              String(
                item.details || ""
              ).slice(0,250)
            )}
          </p>

          <button
            class="main"
            onclick="readNews('${key}')">
            📖 Read Full News
          </button>

          ${
            isAdmin
            ?
            `
            <div class="actions">

              <button
                class="orange"
                onclick="editNews('${key}')">
                Edit
              </button>

              <button
                class="red"
                onclick="deleteNews('${key}')">
                Delete
              </button>

            </div>
            `
            : ""
          }

        </div>

      `;

    }
  );


  if(!html){

    html =
      `
      <div class="card">
        Abhi koi news available nahi hai.
      </div>
      `;

  }


  box.innerHTML =
    html;

}


/* =========================================================
   READ NEWS
========================================================= */

function readNews(key){

  const item =
    newsData[key];


  if(!item)return;


  document.getElementById(
    "modalTitle"
  ).innerText =
    item.title || "";


  document.getElementById(
    "modalDetails"
  ).innerText =
    item.details || "";


  document.getElementById(
    "newsModal"
  ).style.display =
    "block";

}


function closeNews(){

  document.getElementById(
    "newsModal"
  ).style.display =
    "none";

}


/* =========================================================
   EDIT NEWS
========================================================= */

function editNews(key){

  if(!isAdmin)return;


  const item =
    newsData[key];


  const title =
    prompt(
      "News title:",
      item.title || ""
    );


  if(title === null)return;


  const details =
    prompt(
      "News details:",
      item.details || ""
    );


  if(details === null)return;


  db.ref(
    "news/" +
    key
  )
  .update({

    title:title,

    details:details

  });

}


/* =========================================================
   DELETE NEWS
========================================================= */

function deleteNews(key){

  if(!isAdmin)return;


  if(
    !confirm(
      "Kya aap ye news delete karna chahte hain?"
    )
  ){

    return;

  }


  db.ref(
    "news/" +
    key
  ).remove();

}


/* =========================================================
   GALLERY LOAD
========================================================= */

db.ref("gallery")
.on(
  "value",
  snapshot=>{

    galleryData =
      snapshot.val() || {};

    renderGallery();

  }
);


/* =========================================================
   GALLERY UPLOAD
========================================================= */

async function uploadGallery(){

  if(!isAdmin){

    alert(
      "Pehle Admin Login karein."
    );

    return;

  }


  const file =
    document.getElementById(
      "galleryFile"
    ).files[0];


  const title =
    document.getElementById(
      "galleryTitle"
    ).value.trim();


  const status =
    document.getElementById(
      "galleryStatus"
    );


  if(!file){

    alert(
      "Photo select karein."
    );

    return;

  }


  try{

    status.innerText =
      "⏳ Photo upload ho rahi hai...";


    const url =
      await uploadToCloudinary(
        file,
        "image"
      );


    await db.ref(
      "gallery"
    ).push({

      title:
        title ||
        "Gallery Photo",

      url:url,

      createdAt:
        firebase.database
          .ServerValue
          .TIMESTAMP

    });


    document.getElementById(
      "galleryFile"
    ).value = "";


    document.getElementById(
      "galleryTitle"
    ).value = "";


    status.innerText =
      "✅ Photo uploaded successfully.";

  }
  catch(error){

    console.error(error);

    status.innerText =
      "❌ " +
      error.message;

  }

}


/* =========================================================
   RENDER GALLERY
========================================================= */

function renderGallery(){

  const box =
    document.getElementById(
      "galleryList"
    );


  if(!box)return;


  let html = "";


  Object.entries(galleryData)
    .reverse()
    .forEach(
      ([key,item])=>{

        html += `

          <div class="galleryItem">

            <img
              src="${item.url}"
              alt="${escapeHTML(
                item.title || ""
              )}"
              loading="lazy">

            <p>
              <b>
                ${escapeHTML(
                  item.title || ""
                )}
              </b>
            </p>

            ${
              isAdmin
              ?
              `
              <button
                class="main red"
                onclick="deleteGallery('${key}')">
                Delete
              </button>
              `
              : ""
            }

          </div>

        `;

      }
    );


  if(!html){

    html =
      `
      <div class="card">
        Abhi gallery me koi photo nahi hai.
      </div>
      `;

  }


  box.innerHTML =
    html;

}


/* =========================================================
   DELETE GALLERY
========================================================= */

function deleteGallery(key){

  if(!isAdmin)return;


  if(
    !confirm(
      "Kya aap ye gallery photo delete karna chahte hain?"
    )
  ){

    return;

  }


  db.ref(
    "gallery/" +
    key
  ).remove();

}


/* =========================================================
   ESCAPE HTML
========================================================= */

function escapeHTML(value){

  return String(value || "")
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");

}

</script>

</body>
</html>
