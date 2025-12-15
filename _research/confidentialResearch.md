---
title: "Confidential Research"
collection: portfolio
sitemap: false
search: false
---

<div id="login-area">
  <h3>🔒 Restricted Access</h3>
  <p>Please enter the access code to view this project.</p>
  <input type="password" id="password-input" placeholder="Enter Code">
  <button onclick="checkPassword()">Unlock</button>
  <p id="error-msg" style="color:red; display:none;">Incorrect code.</p>
</div>

<div id="protected-content" style="display:none;">

  ## Secret Project Details
  Here is the text that is hidden. You can put images and regular markdown here.
  
  * Result A
  * Result B
  
  [Link to Download Data](#)

</div>

<script>
  function checkPassword() {
    var input = document.getElementById("password-input").value;
    // REPLACE '1234' WITH YOUR DESIRED PASSWORD
    if (input === "1234") { 
      document.getElementById("login-area").style.display = "none";
      document.getElementById("protected-content").style.display = "block";
    } else {
      document.getElementById("error-msg").style.display = "block";
    }
  }
</script>