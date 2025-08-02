# Task-application
Todo app description 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>To-Do List App</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f2f5;
      padding: 50px;
      display: flex;
      justify-content: center;
    }

    .container {
      background: white;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      max-width: 400px;
      width: 100%;
    }

    h2 {
      text-align: center;
      margin-bottom: 20px;
    }

    input[type="text"] {
      width: 70%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 6px;
    }

    button {
      padding: 10px 14px;
      background: #28a745;
      color: white;
      border: none;
      border-radius: 6px;
      margin-left: 5px;
      cursor: pointer;
    }

    ul {
      list-style-type: none;
      padding: 0;
      margin-top: 20px;
    }

    li {
      padding: 10px;
      background: #f8f9fa;
      margin-bottom: 8px;
      border-radius: 6px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    li.completed {
      text-decoration: line-through;
      color: gray;
    }

    .delete {
      background: red;
      padding: 5px 10px;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <div class="container">
    <h2>To-Do List</h2>
    <input type="text" id="taskInput" placeholder="Enter new task..." />
    <button onclick="addTask()">Add</button>

    <ul id="taskList"></ul>
  </div>

  <script>
    function addTask() {
      const input = document.getElementById("taskInput");
      const taskText = input.value.trim();
      if (taskText === "") return;

      const li = document.createElement("li");
      li.textContent = taskText;

      li.onclick = () => li.classList.toggle("completed");

      const delBtn = document.createElement("button");
      delBtn.textContent = "Delete";
      delBtn.className = "delete";
      delBtn.onclick = (e) => {
        e.stopPropagation();
        li.remove();
      };

      li.appendChild(delBtn);
      document.getElementById("taskList").appendChild(li);
      input.value = "";
    }
  </script>

</body>
</html>
