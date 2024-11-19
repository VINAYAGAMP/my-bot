<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chatbot</title>
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .chat-container {
            width: 400px;
            border: 1px solid #ccc;
            border-radius: 10px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .chat-box {
            padding: 10px;
            height: 300px;
            overflow-y: auto;
            border-bottom: 1px solid #ccc;
        }
        .input-container {
            display: flex;
            border-top: 1px solid #ccc;
        }
        .input-container input {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 0 0 0 10px;
        }
        .input-container button {
            padding: 10px;
            border: none;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
            border-radius: 0 0 10px 0;
        }
        .message-container {
            display: flex;
            align-items: flex-start;
            margin-bottom: 10px;
        }
        .message-container img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 10px;
        }
        .user-message-container {
            justify-content: flex-end;
        }
        .user-message-container img {
            margin-right: 0;
            margin-left: 10px;
        }
        .user-message {
            background-color: #e1ffc7;
            padding: 10px;
            border-radius: 5px;
            text-align: right;
            flex: 1;
        }
        .bot-message {
            background-color: #f1f0f0;
            padding: 10px;
            border-radius: 5px;
            text-align: left;
            flex: 1;
        }
    </style>
</head>
<body>
    <div class="container mt-5">
        <div class="card">
            <div class="card-header text-center">
                <h2>Chatbot</h2>
            </div>
            <div class="card-body">
                <div id="chat-box" class="chat-box p-3 mb-3 border rounded">
                    <!-- Chat messages will appear here -->
                </div>
                <div class="input-group">
                    <input type="text" id="user-input" class="form-control" placeholder="Type your message here..." onkeydown="checkEnter(event)">
                    <div class="input-group-append">
                        <button class="btn btn-primary" onclick="sendMessage()">
                            <i class="fa fa-paper-plane"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <script>
        document.addEventListener("DOMContentLoaded", function() {
            const userInput = document.getElementById("user-input");

            // Function to handle sending messages
            function sendMessage() {
                const chatBox = document.getElementById("chat-box");

                // Create a user message element
                const userMessageContainer = document.createElement("div");
                userMessageContainer.className = "message-container user-message-container";

                const userAvatar = document.createElement("img");
                userAvatar.src = "https://cdn-icons-png.flaticon.com/512/21/21104.png";
                userAvatar.alt = "User Avatar";

                const userMessage = document.createElement("div");
                userMessage.className = "user-message";
                userMessage.textContent = userInput.value;

                userMessageContainer.appendChild(userMessage);
                userMessageContainer.appendChild(userAvatar);
                chatBox.appendChild(userMessageContainer);

                // Clear the input field
                userInput.value = "";

                // Create a bot response element
                const botMessageContainer = document.createElement("div");
                botMessageContainer.className = "message-container bot-message-container";

                const botAvatar = document.createElement("img");
                botAvatar.src = "https://tse2.mm.bing.net/th?id=OIP.VWZ7BAZEJcr0PErTzNx2pgHaHa&pid=Api&P=0&h=180";
                botAvatar.alt = "Bot Avatar";

                const botMessage = document.createElement("div");
                botMessage.className = "bot-message";
                botMessage.textContent = "This is a response from the bot.";

                botMessageContainer.appendChild(botAvatar);
                botMessageContainer.appendChild(botMessage);
                chatBox.appendChild(botMessageContainer);

                // Scroll to the bottom of the chat box
                chatBox.scrollTop = chatBox.scrollHeight;
            }

            // Function to check if the Enter key is pressed
            function checkEnter(event) {
                if (event.key === "Enter") {
                    sendMessage();
                }
            }

            // Add event listeners
            userInput.addEventListener("keydown", checkEnter);
            document.querySelector("button").addEventListener("click", sendMessage);
        });
    </script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
</body>
</html>
