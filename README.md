# Week-6
Fronted end website assignments 
Project Structure
/project-folder
 ├── index.html
 ├── style.css
 └── script.js

index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive Web Page</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>My Interactive Web Page</h1>
    <nav>
      <a href="#form">Form</a>
      <a href="#counter">Counter</a>
      <a href="#toggle">Theme Toggle</a>
    </nav>
  </header>

  <main>
    <!-- Interactive Form Section -->
    <section id="form">
      <h2>Contact Form</h2>
      <form id="contactForm">
        <label for="name">Name:</label>
        <input type="text" id="name" placeholder="Enter your name">

        <label for="email">Email:</label>
        <input type="text" id="email" placeholder="Enter your email">

        <label for="message">Message:</label>
        <textarea id="message" placeholder="Type your message"></textarea>

        <button type="submit">Submit</button>
        <p id="formMessage"></p>
      </form>
    </section>

    <!-- Counter Section -->
    <section id="counter">
      <h2>Interactive Counter</h2>
      <p>Current Count: <span id="count">0</span></p>
      <button id="increaseBtn">Increase</button>
      <button id="decreaseBtn">Decrease</button>
      <button id="resetBtn">Reset</button>
    </section>

    <!-- Theme Toggle Section -->
    <section id="toggle">
      <h2>Theme Toggle</h2>
      <p>Click the button below to switch between Light and Dark mode:</p>
      <button id="themeToggle">Toggle Theme</button>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Interactive Demo</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>

style.css
/* General Styling */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background: #f4f4f9;
  color: #333;
}

header {
  background: #0077cc;
  color: #fff;
  padding: 1rem;
  text-align: center;
}

header nav a {
  margin: 0 10px;
  color: #fff;
  text-decoration: none;
}

section {
  padding: 2rem;
  margin: 1rem auto;
  max-width: 600px;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

/* Buttons */
button {
  margin: 5px;
  padding: 10px 15px;
  border: none;
  border-radius: 6px;
  background: #0077cc;
  color: white;
  cursor: pointer;
  transition: 0.3s;
}
button:hover {
  background: #005fa3;
}

/* Form */
form input, form textarea {
  width: 100%;
  padding: 8px;
  margin: 8px 0;
  border: 1px solid #ddd;
  border-radius: 6px;
}

#formMessage {
  margin-top: 10px;
  font-weight: bold;
}

/* Dark Theme */
body.dark {
  background: #1a1a1a;
  color: #eee;
}
body.dark section {
  background: #333;
}
body.dark button {
  background: #555;
}

script.js
// ===============================
// Custom Form Validation
// ===============================
document.getElementById("contactForm").addEventListener("submit", function (e) {
  e.preventDefault(); // Prevent page reload

  let name = document.getElementById("name").value.trim();
  let email = document.getElementById("email").value.trim();
  let message = document.getElementById("message").value.trim();
  let formMessage = document.getElementById("formMessage");

  // Validate inputs
  if (name.length < 3) {
    formMessage.textContent = "Name must be at least 3 characters.";
    formMessage.style.color = "red";
    return;
  }

  if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
    formMessage.textContent = "Please enter a valid email address.";
    formMessage.style.color = "red";
    return;
  }

  if (message.length < 10) {
    formMessage.textContent = "Message must be at least 10 characters.";
    formMessage.style.color = "red";
    return;
  }

  // Success
  formMessage.textContent = "Form submitted successfully!";
  formMessage.style.color = "green";

  // Reset form
  document.getElementById("contactForm").reset();
});

// ===============================
// Interactive Counter Feature
// ===============================
let count = 0;
const countDisplay = document.getElementById("count");

document.getElementById("increaseBtn").addEventListener("click", () => {
  count++;
  countDisplay.textContent = count;
});

document.getElementById("decreaseBtn").addEventListener("click", () => {
  if (count > 0) {
    count--;
    countDisplay.textContent = count;
  }
});

document.getElementById("resetBtn").addEventListener("click", () => {
  count = 0;
  countDisplay.textContent = count;
});

// ===============================
// Theme Toggle Feature
// ===============================
const themeToggle = document.getElementById("themeToggle");

themeToggle.addEventListener("click", () => {
  document.body.classList.toggle("dark");

  if (document.body.classList.contains("dark")) {
    themeToggle.textContent = "Switch to Light Mode";
  } else {
    themeToggle.textContent = "Switch to Dark Mode";
  }
});


