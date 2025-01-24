<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Friend-Bot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .chat-container {
            width: 400px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }
        .chat-box {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            height: 300px;
            border-bottom: 1px solid #ddd;
        }
        .chat-box p {
            margin: 10px 0;
        }
        .chat-box .bot-message {
            color: #4CAF50;
        }
        .chat-box .user-message {
            text-align: right;
            color: #008CBA;
        }
        .input-container {
            display: flex;
            padding: 10px;
            border-top: 1px solid #ddd;
        }
        .input-container input {
            width: 100%;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ddd;
            font-size: 14px;
        }
        .input-container button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            margin-left: 10px;
        }
        .input-container button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

    <div class="chat-container">
        <div class="chat-box" id="chat-box">
            <p class="bot-message">Hello! I'm your Friend-Bot. How are you doing today?</p>
        </div>
        <div class="input-container">
            <input type="text" id="user-input" placeholder="Type a message...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        function sendMessage() {
            const userInput = document.getElementById('user-input').value;
            if (userInput.trim() !== "") {
                // Display user message
                let chatBox = document.getElementById('chat-box');
                let userMessage = document.createElement('p');
                userMessage.classList.add('user-message');
                userMessage.innerText = userInput;
                chatBox.appendChild(userMessage);

                // Clear the input field
                document.getElementById('user-input').value = "";

                // Simulate bot response
                let botMessage = document.createElement('p');
                botMessage.classList.add('bot-message');

                // Simple bot responses
                if (userInput.toLowerCase().includes("how are you")) {
                    botMessage.innerText = "I'm doing great, thanks for asking! How about you?";
                } else if (userInput.toLowerCase().includes("hello")) {
                    botMessage.innerText = "Hey there! How can I help you today?";
                } else if (userInput.toLowerCase().includes("bye")) {
                    botMessage.innerText = "Goodbye! Take care!";
                } else {
                    botMessage.innerText = "Hmm, I'm not sure what to say. Tell me more!";
                }

                // Append bot response
                chatBox.appendChild(botMessage);

                // Scroll to the bottom of the chat box
                chatBox.scrollTop = chatBox.scrollHeight;
            }
        }

        // Allow sending message by pressing "Enter"
        document.getElementById('user-input').addEventListener('keydown', function(event) {
            if (event.key === 'Enter') {
                sendMessage();
            }
        });
    </script>

</body>
</html>
