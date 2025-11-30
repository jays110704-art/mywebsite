
<!DOCTYPE html>
<html>
<head>
  <title>My Test Wallet</title>
  <style>
    body {
      font-family: Arial;
      background: #f5f5f5;
      padding: 30px;
    }
    .box {
      background: white;
      padding: 20px;
      border-radius: 10px;
      width: 300px;
      margin: auto;
      text-align: center;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    button {
      padding: 10px 15px;
      margin: 10px;
      border-radius: 5px;
      border: none;
      cursor: pointer;
    }
    .admin {
      background: #007bff;
      color: white;
    }
    .reset {
      background: #ff4444;
      color: white;
    }
  </style>
</head>
<body>

  <div class="box">
    <h2>Balance: <span id="balance">0</span> Coins</h2>
    <p>Referral Code: <span id="referral">None</span></p>

    <button class="admin" id="addUnlimited">
      Add Unlimited (Admin)
    </button>

    <button class="reset" id="resetBalance">
      Reset Balance
    </button>
  </div>

<script>
// Load saved balance
let balance = Number(localStorage.getItem("balance")) || 0;
document.getElementById("balance").innerText = balance;

// Admin unlimited coins
document.getElementById("addUnlimited").addEventListener("click", function () {
  let pass = prompt("Enter Admin Password:");

  if (pass === "admin123") { 
      balance = 999999999;
      localStorage.setItem("balance", balance);
      document.getElementById("balance").innerText = balance;
      alert("Unlimited balance added!");
  } else {
      alert("Wrong password!");
  }
});

// Reset balance
document.getElementById("resetBalance").addEventListener("click", function () {
  balance = 0;
  localStorage.setItem("balance", balance);
  document.getElementById("balance").innerText = balance;
  alert("Balance reset!");
});

// Referral code support
const urlParams = new URLSearchParams(window.location.search);
const referralCode = urlParams.get('referralCode') || null;

if (referralCode !== null) {
    localStorage.setItem("referral", referralCode);
}

document.getElementById("referral").innerText =
    localStorage.getItem("referral") || "None";
</script>

</body>
</html>
