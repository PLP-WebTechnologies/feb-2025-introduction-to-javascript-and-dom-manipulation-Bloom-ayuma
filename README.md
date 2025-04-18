# Introduction to JavaScript and DOM Manipulation

## Objectives

Write basic JavaScript functions.
Manipulate the DOM dynamically.
Respond to user interactions.

## Instructions

- Create a script.js file and link it to a HTML.
- Structure the document using DOCTYPE, html, head, and body.

>[!NOTE]
>  - Write JavaScript that:
>  - Changes text content dynamically.
>  - Modifies CSS styles via JavaScript.
>  - Adds or removes an element when a button is clicked.


# Tasks
- Create a well-structured HTML5 document.
- Use at least 5 different HTML elements.
- Ensure semantic correctness.

Happy Coding! 💻✨

📁 Folder Structure:
my-dom-project/
├── index.html
├── style.css
└── script.js
📄 index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Interactive DOM</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <h1 id="main-title">Welcome to My Interactive Page</h1>
  </header>

  <main>
    <section>
      <p id="description">Use the buttons and form below to interact with the page!</p>

      <div class="button-group">
        <button id="text-btn">Change Text</button>
        <button id="style-btn">Change Style</button>
        <button id="toggle-btn">Add/Remove Element</button>
      </div>
    </section>

    <section>
      <h2>💬 Send a Message</h2>
      <form id="message-form">
        <input type="text" id="user-input" placeholder="Type something..." required />
        <button type="submit">Submit</button>
      </form>
      <p id="form-output"></p>
    </section>

    <article id="dynamic-area"></article>
  </main>

  <footer>
    <p>&copy; 2025 Interactive DOM Zone</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
🎨 style.css
body {
  font-family: 'Segoe UI', sans-serif;
  padding: 20px;
  background-color: #f8f8f8;
}

h1 {
  color: #333;
}

.button-group button, form button {
  margin: 10px 5px;
  padding: 10px 15px;
  font-size: 1em;
  cursor: pointer;
}

input {
  padding: 8px;
  font-size: 1em;
}

#dynamic-area p {
  background-color: #d1e7dd;
  padding: 10px;
  margin-top: 10px;
  animation: fadeIn 0.5s ease-in-out;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(-10px); }
  to { opacity: 1; transform: translateY(0); }
}
🧠 script.js
document.addEventListener('DOMContentLoaded', () => {
  const title = document.getElementById('main-title');
  const description = document.getElementById('description');
  const dynamicArea = document.getElementById('dynamic-area');
  const form = document.getElementById('message-form');
  const userInput = document.getElementById('user-input');
  const formOutput = document.getElementById('form-output');

  // Event Listeners
  document.getElementById('text-btn').addEventListener('click', () => {
    title.textContent = '🎉 You just changed the title dynamically!';
  });

  document.getElementById('style-btn').addEventListener('click', () => {
    description.style.color = 'darkgreen';
    description.style.backgroundColor = '#e6ffe6';
    description.style.fontSize = '1.2em';
  });

  document.getElementById('toggle-btn').addEventListener('click', () => {
    const existing = document.getElementById('new-paragraph');
    if (existing) {
      existing.remove();
    } else {
      const newPara = document.createElement('p');
      newPara.id = 'new-paragraph';
      newPara.textContent = '✨ A new paragraph fades in with animation!';
      dynamicArea.appendChild(newPara);
    }
  });

  // Form submission
  form.addEventListener('submit', (e) => {
    e.preventDefault();
    const message = userInput.value.trim();
    if (message) {
      formOutput.textContent = `✅ You typed: "${message}"`;
      formOutput.style.color = '#007B55';
      userInput.value = '';
    }
  });
});

