<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Chatbot</title>
</head>
<body>

  <h1>Chatbot</h1>

  <div style="width: 400px; height: 500px; border: 1px solid #ddd; padding: 10px; background-color: #f9f9f9;">
    <div style="height: 450px; overflow-y: scroll; padding: 10px; background-color: #fff;">
      <!-- Chat messages will be shown here -->
      <p><strong>Bot:</strong> Hello! How can I assist you today?</p>
      <p><strong>User:</strong> Hi, I need help.</p>
      <p><strong>Bot:</strong> Sure! What kind of help do you need?</p>
    </div>

    <!-- Input and Send Button (Static) -->
    <form>
      <input type="text" placeholder="Type your message..." style="width: 80%; padding: 10px; margin: 5px 0;">
      <button type="submit" style="padding: 10px 15px; background-color: #4CAF50; color: white; border: none;">Send</button>
    </form>
  </div>

</body>
</html>
