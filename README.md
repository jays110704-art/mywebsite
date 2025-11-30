# mywebsite
it'll be nice for you
<div class="box">
  <h2>Balance: <span id="balance">0</span> Coins</h2>
  <p>Referral Code: <span id="referral">None</span></p> <!-- NEW -->
  
  <button class="admin" id="addUnlimited">
    Add Unlimited (Admin)
  </button>

  <button class="reset" id="resetBalance">
    Reset Balance
  </button>
</div>// Read referral code from URL
const urlParams = new URLSearchParams(window.location.search);
const referralCode = urlParams.get('referralCode') || "None";
document.getElementById("referral").innerText = referralCode;
