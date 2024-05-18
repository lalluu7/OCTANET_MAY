<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>To-Do List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f7f7f7;
        }

        .container {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }

        h1 {
            text-align: center;
            color: #333;
        }

        .task-input {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
        }

        .task-input input {
            flex-grow: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        .task-input button {
            padding: 10px 20px;
            border: none;
            background-color: #28a745;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .task-input button:hover {
            background-color: #218838;
        }

        ul {
            list-style: none;
            padding: 0;
        }

        li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            border-bottom: 1px solid #ddd;
        }

        li.completed {
            text-decoration: line-through;
            color: #aaa;
        }

        li button {
            padding: 5px 10px;
            border: none;
            background-color: #dc3545;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        li button:hover {
            background-color: #c82333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>My To-Do List</h1>
        <div class="task-input">
            <input type="text" id="task" placeholder="Enter a new task...">
            <button id="add-task">Add Task</button>
        </div>
        <ul id="task-list">
            <!-- Tasks will be dynamically inserted here -->
        </ul>
    </div>
    <script>
        // Get references to elements
        const taskInput = document.getElementById("task");
        const addTaskButton = document.getElementById("add-task");
        const taskList = document.getElementById("task-list");

        // Function to add a new task
        function addTask() {
            const taskText = taskInput.value.trim();
            if (taskText === "") {
                return;
            }

            // Create a new list item for the task
            const listItem = document.createElement("li");
            listItem.textContent = taskText;

            // Create "Complete" and "Delete" buttons
            const completeButton = document.createElement("button");
            completeButton.textContent = "Complete";
            completeButton.addEventListener("click", () => {
                listItem.classList.toggle("completed");
            });

            const deleteButton = document.createElement("button");
            deleteButton.textContent = "Delete";
            deleteButton.addEventListener("click", () => {
                taskList.removeChild(listItem);
            });

            // Add buttons to the list item
            listItem.appendChild(completeButton);
            listItem.appendChild(deleteButton);

            // Add the list item to the task list
            taskList.appendChild(listItem);

            // Clear the task input
            taskInput.value = "";
            taskInput.focus();
        }

        // Add task when the "Add Task" button is clicked
        addTaskButton.addEventListener("click", addTask);

        // Add task when Enter key is pressed
        taskInput.addEventListener("keydown", (e) => {
            if (e.key === "Enter") {
                addTask();
            }
        });
    </script>
</body>
</html>
