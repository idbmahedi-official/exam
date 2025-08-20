# exam

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Form Validation</title>
  <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
  <style>
    .popup-box {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      text-align: left;
    }
    .popup-item {
      background: #d9d5d577;
      padding: 8px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .popup-item b {
      display: block;
      color: #444;
      margin-bottom: 4px;
    }

    .title{color: blue;}

    label{font-weight: bold;}
    h1{color: rgb(255, 0, 0);}

   button{width: 170px;
height: 30px;
font-size: large;}

  </style>
</head>
<body>
  <h1>Form Validation</h1>
  
  <form id="form">
    <label>Name:</label><br>
    <input type="text" id="name" required><br><br>

    <label>Password:</label><br>
    <input type="password" id="password" required><br><br>

    <label>Age:</label><br>
    <input type="number" id="age" required><br><br>

    <label>Email:</label><br>
    <input type="email" id="email" required><br><br>

    <label>Phone:</label><br>
    <input type="text" id="phone" required><br><br>

    <label>Gender:</label><br>
    <input type="radio" name="gender" value="Male"> Male
    <input type="radio" name="gender" value="Female"> Female<br><br>

    <label>Choose Country:</label><br>
    <select id="country">
      <option value="Bangladesh">Bangladesh</option>
      <option value="India">India</option>
      <option value="USA">USA</option>
    </select><br><br>

    <label>Choose Your Subject:</label><br>
    <input type="checkbox" name="subject" value="Math"> Math
    <input type="checkbox" name="subject" value="English"> English
    <input type="checkbox" name="subject" value="Physics"> Physics <br><br>

    <button type="submit">Submit</button>
  </form>

  <script>
    document.getElementById("form").addEventListener("submit", function(e){
      e.preventDefault();

      let name = document.getElementById("name").value;
      let password = document.getElementById("password").value;
      let age = document.getElementById("age").value;
      let email = document.getElementById("email").value;
      let phone = document.getElementById("phone").value;
      let gender = document.querySelector('input[name="gender"]:checked')?.value || "Not Selected";
      let country = document.getElementById("country").value;
      let subjects = Array.from(document.querySelectorAll('input[name="subject"]:checked'))
                          .map(s => s.value).join(", ") || "Not Selected";

      // Mask password with asterisks
      let maskedPassword = "*".repeat(password.length);

      Swal.fire({
        title: '<span style="color:green;">Form Submitted!</span>',
        html: `
          <div class="popup-box">
            <div class="popup-item"><b>Name</b> ${name}</div>
            <div class="popup-item"><b>Password</b> ${maskedPassword}</div>
            <div class="popup-item"><b>Age</b> ${age}</div>
            <div class="popup-item"><b>Email</b> ${email}</div>
            <div class="popup-item"><b>Phone</b> ${phone}</div>
            <div class="popup-item"><b>Gender</b> ${gender}</div>
            <div class="popup-item"><b>Country</b> ${country}</div>
            <div class="popup-item"><b>Subject(s)</b> ${subjects}</div>
          </div>
        `,
        icon: "success",
        confirmButtonText: "OK",
        width: 600
      });
    });


    
  </script>
</body>
</html>
