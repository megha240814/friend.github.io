<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Friend Chat Bot</title>
  <style>
    body {
      background-color: #f8d9e7; /* Baby pink background */
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }
    #chat-container {
      width: 60%;
      margin: 50px auto;
      background-color: white;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    #chat-box {
      width: 100%;
      height: 300px;
      overflow-y: scroll;
      border: 1px solid #ccc;
      padding: 10px;
      border-radius: 10px;
      background-color: #f5f5f5;
    }
    .message {
      margin: 10px 0;
    }
    .user-message {
      text-align: right;
      background-color: #e0f7fa;
      padding: 8px;
      border-radius: 10px;
      max-width: 60%;
      margin-left: auto;
    }
    .bot-message {
      text-align: left;
      background-color: #e1bee7;
      padding: 8px;
      border-radius: 10px;
      max-width: 60%;
    }
    #user-input {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border-radius: 10px;
      border: 1px solid #ccc;
    }
    #send-btn {
      padding: 10px 15px;
      background-color: #f06292;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    #send-btn:hover {
      background-color: #d81b60;
    }
    .bot-profile {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      background-image: url('robotic-profile.jpg'); /* Replace with your robot profile image */
      background-size: cover;
      margin-right: 10px;
    }
    .chat-header {
      display: flex;
      align-items: center;
      margin-bottom: 20px;
    }
    .chat-header h2 {
      margin: 0;
    }
  </style>
</head>
<body>
  <div id="chat-container">
    <div class="chat-header">
      <div class="bot-profile"></div>
      <h2>Friend Chat Bot</h2>
    </div>
    <div id="chat-box"></div>
    <textarea id="user-input" placeholder="Type a message..."></textarea>
    <button id="send-btn">Send</button>
  </div>

  <script>
    const chatBox = document.getElementById('chat-box');
    const userInput = document.getElementById('user-input');
    const sendBtn = document.getElementById('send-btn');

    // Gradual message typing
    function typeMessage(element, message, delay = 100) {
      let i = 0;
      element.innerHTML = '';
      function type() {
        if (i < message.length) {
          element.innerHTML += message.charAt(i);
          i++;
          setTimeout(type, delay);
        }
      }
      type();
    }

    // Add message to chat box
    function addMessage(message, sender) {
      const messageDiv = document.createElement('div');
      messageDiv.classList.add('message');
      if (sender === 'user') {
        messageDiv.classList.add('user-message');
        messageDiv.innerText = message;
      } else {
        messageDiv.classList.add('bot-message');
        messageDiv.innerHTML = `<div class="bot-profile"></div><span id="bot-msg">${message}</span>`;
        typeMessage(messageDiv.querySelector('#bot-msg'), message);
      }
      chatBox.appendChild(messageDiv);
      chatBox.scrollTop = chatBox.scrollHeight;
    }

    // Simulate bot response with a slight delay
    function simulateBotResponse(userMessage) {
      const botReply = "Hey, I'm your friendly chat bot! How can I help you today?";
      addMessage(botReply, 'bot');
    }

    function handleUserMessage() {
      const message = userInput.value.trim();
      if (message) {
        addMessage(message, 'user');
        userInput.value = '';
        setTimeout(() => {
          simulateBotResponse(message);
        }, 1000);  // Delay before bot replies
      }
    }

    sendBtn.addEventListener('click', handleUserMessage);

    userInput.addEventListener('keypress', (e) => {
      if (e.key === 'Enter' && !e.shiftKey) {
        e.preventDefault();
        handleUserMessage();
      }
    });

    // Initial Bot Greeting
    simulateBotResponse('');
  </script>
</body>
</html>
