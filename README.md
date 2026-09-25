<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.14.1/firebase-database-compat.js"></script>

<script>
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

firebase.initializeApp(firebaseConfig);

const auth = firebase.auth();
const db = firebase.database();

let confirmationResult = null;
let verifiedPhone = "";
let selectedType = "";

function selectType(type) {
  selectedType = type;

  document.getElementById("choiceBox").style.display = "none";
  document.getElementById("formBox").style.display = "block";

  document.getElementById("formTitle").innerText =
    type === "volunteer"
      ? "🙏 Volunteer Registration"
      : "👥 Committee Member Application";
}

function msg(text, type = "ok") {
  const box = document.getElementById("message");
  box.innerText = text;
  box.className = "msg " + type;
  box.style.display = "block";
}

async function sendOTP() {

  const number = document
    .getElementById("phone")
    .value.trim();

  if (!/^[6-9]\d{9}$/.test(number)) {
    msg("सही 10 digit mobile number डालें।", "error");
    return;
  }

  try {

    if (window.recaptchaVerifier) {
      window.recaptchaVerifier.clear();
    }

    window.recaptchaVerifier =
      new firebase.auth.RecaptchaVerifier(
        "recaptcha-container",
        {
          size: "invisible"
        }
      );

    const phoneNumber = "+91" + number;

    confirmationResult =
      await auth.signInWithPhoneNumber(
        phoneNumber,
        window.recaptchaVerifier
      );

    document.getElementById("otpBox")
      .style.display = "block";

    msg("✅ OTP आपके मोबाइल पर भेज दिया गया है।");

  } catch (error) {

    console.error(error);

    msg(
      "OTP भेजने में समस्या: " + error.message,
      "error"
    );

    if (window.recaptchaVerifier) {
      window.recaptchaVerifier.clear();
      window.recaptchaVerifier = null;
    }
  }
}

async function verifyOTP() {

  const otp =
    document.getElementById("otp").value.trim();

  if (!/^\d{6}$/.test(otp)) {
    msg("6 digit OTP डालें।", "error");
    return;
  }

  if (!confirmationResult) {
    msg("पहले OTP भेजें।", "error");
    return;
  }

  try {

    const result =
      await confirmationResult.confirm(otp);

    verifiedPhone = result.user.phoneNumber;

    document.getElementById("otpBox")
      .style.display = "none";

    document.getElementById("verifiedBox")
      .style.display = "block";

    document.getElementById("sendOtpBtn")
      .style.display = "none";

    document.getElementById("phone").readOnly = true;

    msg("✅ Mobile number verified successfully!");

  } catch (error) {

    console.error(error);

    msg(
      "❌ OTP गलत या expired है।",
      "error"
    );
  }
}

async function submitApplication() {

  if (!verifiedPhone) {
    msg("पहले mobile OTP verify करें।", "error");
    return;
  }

  const name =
    document.getElementById("name").value.trim();

  const address =
    document.getElementById("address").value.trim();

  const reason =
    document.getElementById("reason").value.trim();

  if (!name) {
    msg("नाम डालें।", "error");
    return;
  }

  if (!address) {
    msg("पता डालें।", "error");
    return;
  }

  try {

    await db.ref("applications").push({

      name: name,

      phone: verifiedPhone,

      address: address,

      reason: reason,

      type: selectedType,

      phoneVerified: true,

      status: "pending",

      createdAt:
        firebase.database.ServerValue.TIMESTAMP

    });

    msg(
      "🎉 Application successfully submit हो गया!",
      "ok"
    );

  } catch (error) {

    console.error(error);

    msg(
      "Application submit नहीं हो पाया: " +
      error.message,
      "error"
    );
  }
}
</script>
