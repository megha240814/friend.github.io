<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Chatbot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f1f1f1;
            padding: 20px;
        }

        .chat-container {
            max-width: 500px;
            margin: 0 auto;
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .chat-box {
            max-height: 400px;
            overflow-y: auto;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            padding: 10px;
            border-radius: 5px;
            background-color: #fafafa;
        }

        .chat-input {
            width: 100%;
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .bot-message {
            color: #333;
            font-weight: bold;
            margin: 10px 0;
        }

        .user-message {
            color: #0066cc;
            margin: 10px 0;
        }
    </style>
</head>
<body>

    <div class="chat-container">
        <h2>Chat with our Bot</h2>
        <div class="chat-box" id="chat-box">
            <!-- Chat messages will appear here -->
        </div>
        <input type="text" id="user-input" class="chat-input" placeholder="Type a message..." onkeyup="checkEnter(event)">
    </div>

    <script>
        // Sample responses
        const responses = {
            "hello": "Hi! How can I assist you today?",
            "hi": "Hello! How can I help you?",
            "how are you?": "I'm just a bot, but I'm doing great! How about you?",
            "your name?": "I'm a chatbot created to help you!",
            "bye": "Goodbye! Take care.",
        };

        // Add message to chat box
        function addMessage(message, sender) {
            const chatBox = document.getElementById('chat-box');
            const newMessage = document.createElement('div');
            newMessage.classList.add(sender + '-message');
            newMessage.textContent = message;
            chatBox.appendChild(newMessage);
            chatBox.scrollTop = chatBox.scrollHeight; // Auto-scroll to bottom
        }

        // Bot response function
        function getBotResponse(userInput) {
            // Make the input lowercase for easier matching
            const message = userInput.toLowerCase().trim();
            return responses[message] || "Sorry, I didn't understand that. Can you try again?";
        }

        // Handle user input
        function handleUserInput() {
            const userInputField = document.getElementById('user-input');
            const userInput = userInputField.value.trim();
            if (userInput) {
                addMessage(userInput, 'user');
                const botResponse = getBotResponse(userInput);
                setTimeout(() => addMessage(botResponse, 'bot'), 500); // Delay bot response
            }
            userInputField.value = ''; // Clear input field after submission
        }

        // Check if Enter is pressed to send message
        function checkEnter(event) {
            if (event.key === "Enter") {
                handleUserInput();
            }
        }

        // Initial greeting
        addMessage("Hello! I am your chatbot. How can I help you?", "bot");
    </script>

</body>
</html>
