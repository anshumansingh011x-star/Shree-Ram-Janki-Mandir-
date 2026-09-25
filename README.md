
<!doctype html>
<html lang="hi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">

<title>श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति</title>

<style>
*{box-sizing:border-box}

html{scroll-behavior:smooth}

body{
margin:0;
font-family:Arial,sans-serif;
background:#fff8ef;
color:#25160c;
}

header{
background:linear-gradient(135deg,#651200,#d96b00);
color:white;
padding:18px 16px 70px;
}

nav{
max-width:1100px;
margin:auto;
display:flex;
gap:20px;
align-items:center;
}

nav b{
font-size:20px;
margin-right:auto;
}

nav a{
color:white;
text-decoration:none;
font-weight:bold;
}

.hero{
max-width:1100px;
margin:65px auto 0;
}

.hero small{
font-weight:bold;
letter-spacing:2px;
}

.hero h1{
font-size:clamp(32px,7vw,62px);
line-height:1.08;
margin:12px 0;
}

.hero p{
font-size:18px;
}

.wrap{
max-width:1100px;
margin:auto;
}

section{
max-width:1100px;
margin:auto;
padding:50px 16px;
}

.eyebrow{
font-size:12px;
letter-spacing:2px;
font-weight:800;
color:#a33a00;
}

.choices{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
gap:18px;
}

.choice{
background:white;
border:0;
border-radius:18px;
padding:25px;
text-align:left;
cursor:pointer;
box-shadow:0 8px 28px #0001;
transition:.2s;
}

.choice:hover{
transform:translateY(-3px);
}

.choice span{
font-size:40px;
}

.choice b{
display:block;
font-size:21px;
margin:10px 0;
}

.card,.panel{
background:white;
border-radius:18px;
padding:22px;
box-shadow:0 8px 28px #0001;
}

.hidden{
display:none!important;
}

.grid{
display:grid;
grid-template-columns:1fr 1fr;
gap:15px;
}

label{
font-weight:bold;
}

input,textarea,select{
width:100%;
padding:13px;
margin-top:7px;
border:1px solid #ddd;
border-radius:10px;
font:inherit;
background:#fff;
}

label.full{
grid-column:1/-1;
}

.btn{
display:inline-block;
border:0;
border-radius:10px;
background:#7a1600;
color:white;
padding:13px 19px;
cursor:pointer;
font-weight:bold;
text-decoration:none;
}

.btn:hover{
opacity:.9;
}

.light{
background:#eee;
color:#222;
}

.actions{
display:flex;
gap:10px;
margin-top:20px;
flex-wrap:wrap;
}

.muted{
color:#75665b;
}

.cards{
display:grid;
gap:15px;
}

.gallery{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
gap:15px;
}

.gallery img{
width:100%;
aspect-ratio:1;
object-fit:cover;
border-radius:14px;
display:block;
}

.gallery p{
margin-top:7px;
}

.app{
padding:17px 0;
border-top:1px solid #eee;
line-height:1.7;
}

.danger{
background:#a00000;
color:white;
border:0;
border-radius:8px;
padding:8px 12px;
cursor:pointer;
}

.success{
color:green;
font-weight:bold;
}

.error{
color:#b00000;
font-weight:bold;
}

footer{
background:#24140b;
color:white;
text-align:center;
padding:30px 15px;
line-height:1.7;
}

.admin-box{
display:grid;
gap:15px;
}

.stats{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:12px;
margin:15px 0;
}

.stat{
background:#fff7ed;
padding:15px;
border-radius:12px;
text-align:center;
}

.stat b{
font-size:25px;
display:block;
color:#7a1600;
}

@media(max-width:650px){

nav{
gap:10px;
}

nav b{
font-size:16px;
}

nav a{
font-size:13px;
}

.grid{
grid-template-columns:1fr;
}

label.full{
grid-column:auto;
}

.stats{
grid-template-columns:1fr;
}

.hero{
margin-top:45px;
}

}
</style>
</head>

<body>

<header>

<nav>
<b>श्री राम जानकी मंदिर</b>

<a href="#join">Join</a>
<a href="#newsSection">News</a>
<a href="#gallerySection">Gallery</a>
<a href="#admin">Admin</a>
</nav>

<div class="hero">

<small>SISWA BAZAR</small>

<h1>
श्री राम जानकी मंदिर<br>
दुर्गा पूजा सेवा समिति
</h1>

<p>सेवा • श्रद्धा • सहयोग • संस्कार</p>

<a class="btn" href="#join">
समिति से जुड़ें
</a>

</div>

</header>


<!-- JOIN -->

<section id="join">

<p class="eyebrow">JOIN US</p>

<h2>आप किस रूप में जुड़ना चाहते हैं?</h2>

<div class="choices">

<button class="choice" onclick="openForm('volunteer')">

<span>🙋</span>

<b>Volunteer</b>

<small>
सेवा कार्यों में सहयोग करें
</small>

</button>


<button class="choice" onclick="openForm('committee')">

<span>🪔</span>

<b>Committee Member</b>

<small>
समिति में जिम्मेदारी के लिए आवेदन
</small>

</button>

</div>

</section>


<!-- FORM -->

<section id="formBox" class="hidden">

<p class="eyebrow" id="typeLabel"></p>

<h2 id="formTitle"></h2>

<form id="joinForm">

<input type="hidden" id="type">

<div class="grid">

<label>
पूरा नाम
<input id="name" required>
</label>


<label>
मोबाइल नंबर
<input id="phone" required inputmode="tel">
</label>


<label>
उम्र
<input id="age" required type="number" min="10" max="100">
</label>


<label>
पता
<input id="address" required>
</label>


<label class="full">
सेवा/जिम्मेदारी में रुचि
<textarea id="interest" rows="3"
placeholder="जैसे: व्यवस्था, प्रसाद, सजावट, सुरक्षा आदि"></textarea>
</label>


<label class="full" id="idWrap">

Previous ID Card

<input
id="idCard"
type="file"
accept="image/*,.pdf"
>

<small class="muted">
केवल Volunteer के लिए • अधिकतम 500KB
</small>

</label>

</div>


<div class="actions">

<button class="btn">
Submit Application
</button>

<button
type="button"
class="btn light"
onclick="closeForm()">
Back
</button>

</div>

<p id="formMsg"></p>

</form>

</section>


<!-- NEWS -->

<section id="newsSection">

<p class="eyebrow">UPDATES</p>

<h2>News & Announcements</h2>

<div id="news" class="cards">

<p class="muted">
Loading...
</p>

</div>

</section>


<!-- GALLERY -->

<section id="gallerySection">

<p class="eyebrow">MEMORIES</p>

<h2>Gallery</h2>

<div id="gallery" class="gallery">

<p class="muted">
Loading...
</p>

</div>

</section>


<!-- ADMIN -->

<section id="admin">

<p class="eyebrow">ADMIN</p>

<h2>Admin Panel</h2>


<!-- LOGIN -->

<div id="login" class="panel">

<p>
🔐 Password-only Admin Access
</p>

<input
id="pass"
type="password"
placeholder="Admin password"
>

<button
class="btn"
onclick="adminLogin()">
Login
</button>

<p id="loginMsg"></p>

</div>


<!-- ADMIN PANEL -->

<div id="adminPanel" class="hidden">


<div class="stats">

<div class="stat">
<b id="totalApps">0</b>
Applications
</div>

<div class="stat">
<b id="totalVolunteers">0</b>
Volunteers
</div>

<div class="stat">
<b id="totalCommittee">0</b>
Committee
</div>

</div>


<!-- APPLICATIONS -->

<div class="panel">

<h3>📋 Applications</h3>

<div class="actions">

<button class="btn"
onclick="filterApps('all')">
All
</button>

<button class="btn"
onclick="filterApps('volunteer')">
Volunteers
</button>

<button class="btn"
onclick="filterApps('committee')">
Committee
</button>

</div>

<div id="apps"></div>

</div>


<br>


<!-- NEWS ADMIN -->

<div class="panel">

<h3>📰 Add News</h3>

<input
id="newsTitle"
placeholder="News title"
>

<textarea
id="newsBody"
rows="4"
placeholder="Announcement"
></textarea>

<button
class="btn"
onclick="publishNews()">
Publish News
</button>

</div>


<br>


<!-- GALLERY ADMIN -->

<div class="panel">

<h3>🖼️ Add Gallery Photo</h3>

<input
id="photoCaption"
placeholder="Photo caption"
>

<input
id="photoUrl"
placeholder="Public image URL"
>

<button
class="btn"
onclick="publishPhoto()">
Add Photo
</button>

<p class="muted">
Photo URL डालकर gallery में फोटो जोड़ सकते हैं।
</p>

</div>


</div>

</section>


<footer>

श्री राम जानकी मंदिर दुर्गा पूजा सेवा समिति

<br>

Siswa Bazar

<br>

© <span id="year"></span>

</footer>


<script type="module">

import {
initializeApp
} from
"https://www.gstatic.com/firebasejs/12.2.1/firebase-app.js";


import {
getDatabase,
ref,
push,
onValue,
remove
} from
"https://www.gstatic.com/firebasejs/12.2.1/firebase-database.js";


/* FIREBASE CONFIG */

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


const app = initializeApp(firebaseConfig);

const db = getDatabase(app);


/*
IMPORTANT:
This is only basic client-side protection.
Later we should move admin authentication
to Firebase Authentication.
*/

const ADMIN_PASSWORD = "12345678";


let applications = {};

let currentFilter = "all";


/* SHORT ID FUNCTION */

const $ = id => document.getElementById(id);


/* OPEN FORM */

window.openForm = function(type){

$("formBox").classList.remove("hidden");

$("type").value = type;


if(type === "volunteer"){

$("typeLabel").textContent = "VOLUNTEER";

$("formTitle").textContent =
"Volunteer Application";

$("idWrap").style.display = "block";

}

else{

$("typeLabel").textContent =
"COMMITTEE MEMBER";

$("formTitle").textContent =
"Committee Member Application";

$("idWrap").style.display = "none";

}


$("formMsg").textContent = "";

location.hash = "formBox";

};


/* CLOSE FORM */

window.closeForm = function(){

$("formBox").classList.add("hidden");

};


/* FORM SUBMIT */

$("joinForm").addEventListener(
"submit",
async function(e){

e.preventDefault();

$("formMsg").textContent =
"Submitting...";

$("formMsg").className = "";


try{

let file =
$("idCard").files[0];

let encoded = "";


/* ID CARD */

if(file){

if(file.size > 500000){

$("formMsg").textContent =
"❌ ID card 500KB से कम रखें।";

$("formMsg").className = "error";

return;

}


encoded =
await new Promise(
(resolve,reject)=>{

const reader =
new FileReader();

reader.onload =
() => resolve(reader.result);

reader.onerror =
reject;

reader.readAsDataURL(file);

});

}


/* DATA */

const application = {

type:
$("type").value,

name:
$("name").value.trim(),

phone:
$("phone").value.trim(),

age:
$("age").value,

address:
$("address").value.trim(),

interest:
$("interest").value.trim(),

idCard:
encoded,

createdAt:
Date.now()

};


/* SAVE */

await push(
ref(db,"applications"),
application
);


/* RESET */

$("joinForm").reset();


$("formMsg").textContent =
"✅ Application successfully submit हो गया!";

$("formMsg").className =
"success";


}

catch(error){

console.error(error);

$("formMsg").textContent =
"❌ Submit नहीं हुआ: " +
error.message;

$("formMsg").className =
"error";

}

});


/* APPLICATIONS */

onValue(
ref(db,"applications"),
snapshot => {

applications =
snapshot.val() || {};

renderApps();

updateStats();

});


/* NEWS */

onValue(
ref(db,"news"),
snapshot => {

let list =
Object.values(
snapshot.val() || {}
);


list.sort(
(a,b)=>
(b.createdAt || 0) -
(a.createdAt || 0)
);


if(!list.length){

$("news").innerHTML =
"<p class='muted'>अभी कोई समाचार नहीं।</p>";

return;

}


$("news").innerHTML =
list.map(item => `

<article class="card">

<h3>
${esc(item.title)}
</h3>

<p>
${esc(item.body)}
</p>

</article>

`).join("");

});


/* GALLERY */

onValue(
ref(db,"gallery"),
snapshot => {

let list =
Object.values(
snapshot.val() || {}
);


list.sort(
(a,b)=>
(b.createdAt || 0) -
(a.createdAt || 0)
);


if(!list.length){

$("gallery").innerHTML =
"<p class='muted'>अभी कोई फोटो नहीं।</p>";

return;

}


$("gallery").innerHTML =
list.map(item => {

let safeUrl =
safeImageUrl(item.url);

if(!safeUrl){

return "";

}

return `

<div>

<img
src="${esc(safeUrl)}"
alt="${esc(item.caption || "Gallery photo")}"
loading="lazy"
>

<p>
${esc(item.caption || "")}
</p>

</div>

`;

}).join("");

});


/* ADMIN LOGIN */

window.adminLogin = function(){

const password =
$("pass").value;


if(password === ADMIN_PASSWORD){

$("login").classList.add("hidden");

$("adminPanel").classList.remove("hidden");

$("loginMsg").textContent = "";

renderApps();

updateStats();

}

else{

$("loginMsg").textContent =
"❌ Wrong password";

$("loginMsg").className =
"error";

}

};


/* FILTER */

window.filterApps = function(type){

currentFilter = type;

renderApps();

};


/* RENDER APPLICATIONS */

function renderApps(){

if(!$("apps")) return;


let list =
Object.entries(applications);


list =
list.filter(
([id,item]) =>
currentFilter === "all" ||
item.type === currentFilter
);


list.sort(
(a,b)=>
(b[1].createdAt || 0) -
(a[1].createdAt || 0)
);


if(!list.length){

$("apps").innerHTML =
"<p class='muted'>No applications.</p>";

return;

}


$("apps").innerHTML =
list.map(
([id,item]) => `

<div class="app">

<b>
${esc(item.name)}
</b>

<br>

Type:
${item.type === "volunteer"
? "🙋 Volunteer"
: "🪔 Committee Member"}

<br>

📞 ${esc(item.phone)}

&nbsp; | &nbsp;

Age:
${esc(item.age)}

<br>

📍 ${esc(item.address)}

<br>

${esc(item.interest || "")}

${item.idCard ? `

<br>

<a
href="${item.idCard}"
target="_blank"
rel="noopener">
📄 Previous ID Card देखें
</a>

` : ""}

<br><br>

<button
class="danger"
onclick="deleteApplication('${id}')">
Delete
</button>

</div>

`
).join("");

}


/* DELETE */

window.deleteApplication =
async function(id){

if(
confirm(
"क्या आप यह application delete करना चाहते हैं?"
)
){

await remove(
ref(
db,
"applications/" + id
)
);

}

};


/* NEWS */

window.publishNews =
async function(){

const title =
$("newsTitle").value.trim();

const body =
$("newsBody").value.trim();


if(!title){

alert("Title डालें");

return;

}


await push(
ref(db,"news"),
{

title:title,

body:body,

createdAt:Date.now()

});


$("newsTitle").value = "";

$("newsBody").value = "";

alert("✅ News publish हो गई!");

};


/* GALLERY */

window.publishPhoto =
async function(){

const url =
$("photoUrl").value.trim();

const caption =
$("photoCaption").value.trim();


if(!url){

alert("Image URL डालें");

return;

}


const safe =
safeImageUrl(url);


if(!safe){

alert(
"Valid image URL डालें।"
);

return;

}


await push(
ref(db,"gallery"),
{

url:safe,

caption:caption,

createdAt:Date.now()

});


$("photoUrl").value = "";

$("photoCaption").value = "";

alert("✅ Photo gallery में add हो गई!");

};


/* STATS */

function updateStats(){

let list =
Object.values(applications);


let volunteers =
list.filter(
x => x.type === "volunteer"
).length;


let committee =
list.filter(
x => x.type === "committee"
).length;


$("totalApps").textContent =
list.length;

$("totalVolunteers").textContent =
volunteers;

$("totalCommittee").textContent =
committee;

}


/* SECURITY ESCAPE */

function esc(value = ""){

return String(value)
.replace(
/[&<>"']/g,

function(match){

return {

"&":"&amp;",
"<":"&lt;",
">":"&gt;",
'"':"&quot;",
"'":"&#39;"

}[match];

});

}


/* IMAGE URL CHECK */

function safeImageUrl(value){

try{

const url =
new URL(value);


if(
url.protocol !== "http:" &&
url.protocol !== "https:"
){

return "";

}


return url.href;

}

catch{

return "";

}

}


/* YEAR */

$("year").textContent =
new Date().getFullYear();

</script>

</body>
</html>
