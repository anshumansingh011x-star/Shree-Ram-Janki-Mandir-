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
  databaseURL: "https://shree-ram-janki-mandir-durga-default-rtdb.asia
