<!-- Firebase OTP + Database -->
<script type="module">

import { initializeApp }
from "https://www.gstatic.com/firebasejs/12.2.1/firebase-app.js";

import {
  getDatabase,
  ref,
  push,
  onValue,
  remove,
  update
} from "https://www.gstatic.com/firebasejs/12.2.1/firebase-database.js";

import {
  getAuth,
  RecaptchaVerifier,
  signInWithPhoneNumber
} from "https://www.gstatic.com/firebasejs/12.2.1/firebase-auth.js";


/* ================================
   FIREBASE CONFIG
================================ */

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


/* ================================
   FIREBASE INITIALIZE
================================ */

const app = initializeApp(firebaseConfig);

const db = getDatabase(app);

const auth = getAuth(app);


/* ================================
   ADMIN PASSWORD
================================ */

const ADMIN_PASSWORD = "SRJM2026";


/* ================================
   VARIABLES
================================ */

let confirmationResult = null;

let recaptchaVerifier = null;

let verifiedPhone = "";

let applications = {};

let currentFilter = "all";


/* ================================
   SHORT SELECTOR
================================ */

const $ = id => document.getElementById(id);


/* ================================
   FORM TYPE
================================ */

window.openForm = function(type) {

  $("formBox").classList.remove("hidden");

  $("type").value = type;

  $("typeLabel").textContent =
    type === "volunteer"
    ? "VOLUNTEER"
    : "COMMITTEE MEMBER";

  $("formTitle").textContent =
    type === "volunteer"
    ? "Volunteer Application"
    : "Committee Member Application";

  $("idWrap").style.display =
    type === "volunteer"
    ? "block"
    : "none";

  resetOTP();

  location.hash = "formBox";
};


/* ================================
   CLOSE FORM
================================ */

window.closeForm = function() {

  $("formBox").classList.add("hidden");

};


/* ================================
   RESET OTP
================================ */

function resetOTP() {

  confirmationResult = null;

  verifiedPhone = "";

  $("submitBtn").disabled = true;

  $("phone").readOnly = false;

  $("otpInputBox").classList.add("hidden");

  $("otpMsg").textContent = "";

}


/* ================================
   CREATE RECAPTCHA
================================ */

async function createRecaptcha() {

  if (recaptchaVerifier) return;

  recaptchaVerifier =
    new RecaptchaVerifier(
      auth,
      "recaptcha-container",
      {
        size: "invisible"
      }
    );

  await recaptchaVerifier.render();

}


/* ================================
   SEND OTP
================================ */

window.sendOTP = async function() {

  const phone =
    $("phone").value.trim();


  if (!/^[6-9][0-9]{9}$/.test(phone)) {

    $("otpMsg").className =
      "msg err";

    $("otpMsg").textContent =
      "❌ सही 10 digit Indian mobile number डालें।";

    return;

  }


  $("sendOtpBtn").disabled = true;

  $("otpMsg").className =
    "msg";

  $("otpMsg").textContent =
    "OTP भेजा जा रहा है...";


  try {

    await createRecaptcha();


    confirmationResult =
      await signInWithPhoneNumber(
        auth,
        "+91" + phone,
        recaptchaVerifier
      );


    $("otpInputBox")
      .classList.remove("hidden");


    $("otpMsg").className =
      "msg ok";

    $("otpMsg").textContent =
      "✅ OTP आपके मोबाइल पर भेज दिया गया है।";


  } catch(error) {

    console.error(error);


    $("otpMsg").className =
      "msg err";

    $("otpMsg").textContent =
      "❌ OTP भेजने में समस्या हुई। Firebase Phone Authentication और Authorized Domain check करें।";


    if (recaptchaVerifier) {

      recaptchaVerifier.clear();

      recaptchaVerifier = null;

    }

  }


  $("sendOtpBtn").disabled = false;

};


/* ================================
   VERIFY OTP
================================ */

window.verifyOTP = async function() {

  const otp =
    $("otp").value.trim();


  if (!/^[0-9]{6}$/.test(otp)) {

    $("otpMsg").className =
      "msg err";

    $("otpMsg").textContent =
      "❌ 6 digit OTP डालें।";

    return;

  }


  if (!confirmationResult) {

    $("otpMsg").className =
      "msg err";

    $("otpMsg").textContent =
      "❌ पहले OTP भेजें।";

    return;

  }


  try {

    const result =
      await confirmationResult.confirm(otp);


    verifiedPhone =
      result.user.phoneNumber;


    $("phone").readOnly = true;


    $("otpInputBox")
      .classList.add("hidden");


    $("submitBtn").disabled = false;


    $("otpMsg").className =
      "msg ok";

    $("otpMsg").textContent =
      "✅ Mobile number successfully verified!";


  } catch(error) {

    console.error(error);


    $("otpMsg").className =
      "msg err";

    $("otpMsg").textContent =
      "❌ OTP गलत या expired है।";

  }

};


/* ================================
   SUBMIT APPLICATION
================================ */

$("joinForm").addEventListener(
  "submit",
  async function(e) {

    e.preventDefault();


    if (!verifiedPhone) {

      $("formMsg").className =
        "msg err";

      $("formMsg").textContent =
        "❌ पहले mobile OTP verify करें।";

      return;

    }


    $("submitBtn").disabled = true;

    $("formMsg").textContent =
      "Submitting...";


    let file =
      $("idCard").files[0];

    let idCard = "";


    try {

      if (file) {

        if (file.size > 500000) {

          $("formMsg").className =
            "msg err";

          $("formMsg").textContent =
            "❌ ID Card 500KB से कम रखें।";

          $("submitBtn").disabled = false;

          return;

        }


        idCard =
          await new Promise(
            (resolve, reject) => {

              const reader =
                new FileReader();

              reader.onload =
                () => resolve(reader.result);

              reader.onerror =
                reject;

              reader.readAsDataURL(file);

            }
          );

      }


      await push(
        ref(db, "applications"),
        {

          type:
            $("type").value,

          name:
            $("name").value.trim(),

          phone:
            verifiedPhone,

          phoneVerified:
            true,

          age:
            $("age").value,

          address:
            $("address").value.trim(),

          interest:
            $("interest").value.trim(),

          idCard:
            idCard,

          status:
            "pending",

          createdAt:
            Date.now()

        }
      );


      $("joinForm").reset();

      resetOTP();


      $("formMsg").className =
        "msg ok";

      $("formMsg").textContent =
        "🎉 Application successfully submit हो गया!";


    } catch(error) {

      console.error(error);


      $("formMsg").className =
        "msg err";

      $("formMsg").textContent =
        "❌ Application submit नहीं हुआ।";


      $("submitBtn").disabled =
        false;

    }

  }
);


/* ================================
   ADMIN LOGIN
================================ */

window.adminLogin = function() {

  const password =
    $("pass").value;


  if (password === ADMIN_PASSWORD) {

    $("login")
      .classList.add("hidden");

    $("adminPanel")
      .classList.remove("hidden");


    loadApplications();


  } else {

    $("loginMsg").textContent =
      "❌ Wrong password";

  }

};


/* ================================
   LOAD APPLICATIONS
================================ */

function loadApplications() {

  onValue(
    ref(db, "applications"),
    snapshot => {

      applications =
        snapshot.val() || {};

      renderApplications();

    }
  );

}


/* ================================
   FILTER
================================ */

window.filterApps = function(filter) {

  currentFilter =
    filter;

  renderApplications();

};


/* ================================
   RENDER APPLICATIONS
================================ */

function renderApplications() {

  const list =
    Object.entries(applications)
    .filter(
      ([id, app]) =>
        currentFilter === "all" ||
        app.type === currentFilter
    )
    .sort(
      (a,b) =>
        (b[1].createdAt || 0) -
        (a[1].createdAt || 0)
    );


  $("apps").innerHTML =
    list.length

    ?

    list.map(
      ([id,app]) => `

      <div class="app">

        <b>${esc(app.name)}</b>

        <br>

        Type:
        ${esc(app.type)}

        <br>

        📞
        ${esc(app.phone)}

        ${app.phoneVerified
          ? " • ✅ OTP Verified"
          : ""}

        <br>

        Age:
        ${esc(app.age)}

        <br>

        📍
        ${esc(app.address)}

        <br>

        ${esc(app.interest || "")}

        <br><br>

        <span class="status">

          ${(app.status || "pending").toUpperCase()}

        </span>

        <div class="actions">

          <button
            class="btn success"
            onclick="setStatus('${id}','accepted')">

            Accept

          </button>

          <button
            class="btn danger"
            onclick="setStatus('${id}','rejected')">

            Reject

          </button>

          <button
            class="danger"
            onclick="deleteApplication('${id}')">

            Delete

          </button>

        </div>

      </div>

      `
    ).join("")

    :

    "<p class='muted'>No applications.</p>";

}


/* ================================
   ACCEPT / REJECT
================================ */

window.setStatus =
async function(id,status) {

  await update(
    ref(db, "applications/" + id),
    {

      status:
        status,

      reviewedAt:
        Date.now()

    }
  );

};


/* ================================
   DELETE
================================ */

window.deleteApplication =
async function(id) {

  if (
    confirm(
      "Delete this application?"
    )
  ) {

    await remove(
      ref(
        db,
        "applications/" + id
      )
    );

  }

};


/* ================================
   PUBLISH NEWS
================================ */

window.publishNews =
async function() {

  const title =
    $("newsTitle").value.trim();

  const body =
    $("newsBody").value.trim();


  if (!title) {

    alert("Title डालें");

    return;

  }


  await push(
    ref(db, "news"),
    {

      title:
        title,

      body:
        body,

      createdAt:
        Date.now()

    }
  );


  $("newsTitle").value = "";

  $("newsBody").value = "";

};


/* ================================
   GALLERY
================================ */

window.publishPhoto =
async function() {

  const url =
    $("photoUrl").value.trim();

  const caption =
    $("photoCaption").value.trim();


  if (!url) {

    alert(
      "Image URL डालें"
    );

    return;

  }


  await push(
    ref(db, "gallery"),
    {

      url:
        url,

      caption:
        caption,

      createdAt:
        Date.now()

    }
  );


  $("photoUrl").value = "";

  $("photoCaption").value = "";

};


/* ================================
   ESCAPE HTML
================================ */

function esc(value = "") {

  return String(value)
    .replace(
      /[&<>"']/g,
      char => ({

        "&":"&amp;",
        "<":"&lt;",
        ">":"&gt;",
        '"':"&quot;",
        "'":"&#39;"

      }[char])
    );

}


$("year").textContent =
  new Date().getFullYear();

</script>
