<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Todo-List</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      font-family: fantasy;
      box-sizing: border-box;
    }
    body {
      width: 100vw;
      height: 100vh;
      background-image: linear-gradient(145deg, #a1c4fd 0%, #c2e9fb 100%);
      display: flex;
      justify-content: center;
      align-items: start;
    }
    .listBox {
      padding: 10px;
      min-height: 150px;
      margin-top: 50px;
      box-shadow: 10px 10px 60px #00000050;
      border: 1px solid gray;
      background-image: linear-gradient(to right, #4facfe 0%, #00f2fe 100%);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 20px;
      border-radius: 5px;
    }
    h2 {
      letter-spacing: 2px;
      color: white;
      text-shadow: 5px 5px 10px gray;
    }
    input[type="text"] {
      height: 30px;
      width: 220px;
      padding: 5px;
      border: 1.5px solid;
      border-radius: 5px;
    }
    #sub {
      height: 25px;
      width: 90px;
      color: green;
      border: 1.5px solid gray;
      border-radius: 5px;
    }
    .checker {
      width: 100%;
      display: flex;
      align-items: center;
      gap: 10px;
      justify-content: space-between;
      background: #ffffff60;
      padding: 5px;
      border-radius: 5px;
    }
    #ch {
      height: 20px;
      width: 20px;
    }
    .reset {
      height: 25px;
      width: 25px;
      border-radius: 50%;
      border: none;
      background: #ff4d4d;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <div class="listBox">
    <h2>Todo-List</h2>
    <div class="listText">
      <input type="text" placeholder="Add your list" id="taskInput">
    </div>
    <input type="submit" value="Add Text" id="sub">
  </div>

  <script>
    let box = document.querySelector('.listBox');
    let text = document.querySelector('#taskInput');
    let btn = document.querySelector('#sub');

    btn.addEventListener('click', function() {
      let task = text.value.trim();
      if (task === "") return; // stop if empty

      // Create task container
      let checker = document.createElement('div');
      checker.classList = 'checker';

      // Checkbox
      let ch = document.createElement('input');
      ch.type = 'checkbox';
      ch.id = 'ch';

      // Task text
      let span = document.createElement('span');
      span.textContent = task;

      // Reset button (delete)
      let res = document.createElement('button');
      res.classList = 'reset';
      res.textContent = 'x';

      // Add to container
      checker.appendChild(ch);
      checker.appendChild(span);
      checker.appendChild(res);
      box.appendChild(checker);

      // Clear input
      text.value = '';

      // Checkbox click
      ch.addEventListener('click', function() {
        span.style.textDecoration = ch.checked ? 'line-through' : 'none';
      });

      // Delete button click
      res.addEventListener('click', function() {
        checker.remove();
      });
    });
  </script>

</body>
</html>
