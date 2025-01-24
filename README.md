<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Friend-Bot</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #f3f4f9;
            height: 100vh;
        }
        .chat-container {
            width: 350px;
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }
        .chat-header {
            background-color: #4CAF50;
            padding: 15px;
            color: white;
            font-size: 18px;
            text-align: center;
            font-weight: bold;
        }
        .chat-box {
            flex: 1;
            padding: 15px;
            height: 300px;
            overflow-y: auto;
            background-color: #f9f9f9;
            display: flex;
            flex-direction: column;
        }
        .chat-box p {
            margin: 10px 0;
            padding: 8px;
            border-radius: 5px;
            max-width: 80%;
        }
        .bot-message {
            background-color: #4CAF50;
            color: white;
            align-self: flex-start;
            border-radius: 10px 10px 0 10px;
            margin-left: 10px;
        }
        .user-message {
            background-color: #008CBA;
            color: white;
            align-self: flex-end;
            border-radius: 10px 10px 10px 0;
            margin-right: 10px;
        }
        .input-container {
            display: flex;
            padding: 10px;
            background-color: #ffffff;
            border-top: 1px solid #ddd;
        }
        .input-container input {
            width: 100%;
            padding: 12px;
            border-radius: 5px;
            border: 1px solid #ddd;
            font-size: 14px;
        }
        .input-container button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 12px;
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
        <div class="chat-header">
            Your Friend-Bot
        </div>
        <div class="chat-box" id="chat-box">
            <p class="bot-message">Hey! It's me, your friend 😊. How's your day going?</p>
        </div>
        <div class="input-container">
            <input type="text" id="user-input" placeholder="Tell me something..." autocomplete="off">
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

                // Custom responses based on user input
                if (userInput.toLowerCase().includes("how are you")) {
                    botMessage.innerText = "I'm feeling great, thank you! And you? 😊";
                } else if (userInput.toLowerCase().includes("hello") || userInput.toLowerCase().includes("hi")) {
                    botMessage.innerText = "Heyyy! How's it going? 😄";
                } else if (userInput.toLowerCase().includes("bye")) {
                    botMessage.innerText = "Aww, you're leaving already? Take care, talk soon! 👋";
                } else if (userInput.toLowerCase().includes("what's up") || userInput.toLowerCase().includes("how's life")) {
                    botMessage.innerText = "Just chilling here, you know, the usual 😎. What's up with you?";
                } else if (userInput.toLowerCase().includes("thanks") || userInput.toLowerCase().includes("thank you")) {
                    botMessage.innerText = "You're welcome! Always here for you 😊!";
                } else {
                    botMessage.innerText = "Haha, that's interesting! Tell me more! 😄";
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
