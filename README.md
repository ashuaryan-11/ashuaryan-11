-<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Chat App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="chat-container">
        <div class="messages" id="messages"></div>
        <input type="text" id="messageInput" placeholder="Type your message..." />
        <button onclick="sendMessage()">Send</button>
    </div>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f4f4f4;
    margin: 0;
}

.chat-container {
    width: 400px;
    border: 1px solid #ddd;
    border-radius: 5px;
    background-color: #fff;
    display: flex;
    flex-direction: column;
    height: 500px;
}

.messages {
    flex: 1;
    overflow-y: auto;
    padding: 10px;
    border-bottom: 1px solid #ddd;
}

.message {
    padding: 5px;
    border-bottom: 1px solid #ddd;
}

input {
    border: none;
    padding: 10px;
    flex: 1;
}

button {
    border: none;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}
// Get elements
const messagesDiv = document.getElementById('messages');
const messageInput = document.getElementById('messageInput');

// Function to send message
function sendMessage() {
    const messageText = messageInput.value.trim();
    if (messageText) {
        // Create a new message div
        const messageDiv = document.createElement('div');
        messageDiv.classList.add('message');
        messageDiv.textContent = messageText;

        // Add message to messages container
        messagesDiv.appendChild(messageDiv);

        // Clear input field
        messageInput.value = '';

        // Scroll to the bottom
        messagesDiv.scrollTop = messagesDiv.scrollHeight;
    }
}

// Optional: Send message on Enter key press
messageInput.addEventListener('keypress', function (event) {
    if (event.key === 'Enter') {
        sendMessage();
        event.preventDefault();
    }
});

