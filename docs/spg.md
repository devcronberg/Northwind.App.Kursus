---
created: 2026-01-10
modified: 2026-01-10
author: Michell Cronberg
---
# Eventuelle spørgsmål

Brug denne formular til at stille spørgsmål eller komme med feedback. Jeg spørger for at opdatere denne sider med både spørgsmål og svar.

<form id="my-form" action="https://formspree.io/f/xojjqzpq" method="POST" style="width: 100%;">
  
  <div style="margin-bottom: 15px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px;">Navn:</label>
    <input type="text" name="name" style="width: 100%; display: block; padding: 10px; box-sizing: border-box; border: 2px solid #777; background-color: #fff; color: #000; border-radius: 4px;" />
  </div>

  <div style="margin-bottom: 15px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px;">Spørgsmål:</label>
    <textarea name="message" style="width: 100%; display: block; min-height: 150px; padding: 10px; box-sizing: border-box; border: 2px solid #777; background-color: #fff; color: #000; border-radius: 4px; font-family: inherit;"></textarea>
  </div>

  <button id="my-form-button" style="padding: 10px 24px; background-color: #e91e63; color: white; border: none; border-radius: 4px; cursor: pointer; font-size: 1rem; font-weight: bold;">Send</button>
  <p id="my-form-status"></p>
</form>

<!-- Place this script at the end of the body tag -->
<script>
  var form = document.getElementById("my-form");
  
  async function handleSubmit(event) {
    event.preventDefault();
    var status = document.getElementById("my-form-status");
    var data = new FormData(event.target);
    fetch(event.target.action, {
      method: form.method,
      body: data,
      headers: {
          'Accept': 'application/json'
      }
    }).then(response => {
      if (response.ok) {
        status.innerHTML = "Tak - dit spørgsmål er modtaget!";
        form.reset()
      } else {
        response.json().then(data => {
          if (Object.hasOwn(data, 'errors')) {
            status.innerHTML = data["errors"].map(error => error["message"]).join(", ")
          } else {
            status.innerHTML = "Ups! Der opstod et problem med at sende din formular"
          }
        })
      }
    }).catch(error => {
      status.innerHTML = "Ups! Der opstod et problem med at sende din formular"
    });
  }
  form.addEventListener("submit", handleSubmit)
</script>