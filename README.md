<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Physiotherapy AI Assistant</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f2f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            width: 100%;
            max-width: 600px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #1877f2;
        }
        .chatbox {
            margin-top: 20px;
            padding: 20px;
            background-color: #f9f9f9;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            height: 300px;
            overflow-y: auto;
        }
        .user-msg, .ai-msg {
            margin: 10px 0;
            padding: 10px;
            border-radius: 5px;
            max-width: 80%;
        }
        .user-msg {
            background-color: #dcf8c6;
            margin-left: 20px;
            text-align: left;
        }
        .ai-msg {
            background-color: #fff;
            margin-right: 20px;
            text-align: right;
        }
        input[type="text"] {
            width: calc(100% - 50px);
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #1877f2;
            color: white;
            cursor: pointer;
            margin-left: 10px;
        }
        button:hover {
            background-color: #166fe5;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Physiotherapy AI Assistant</h1>
    <div class="chatbox" id="chatbox"></div>
    <div>
        <input type="text" id="userInput" placeholder="Describe your problem..." />
        <button onclick="handleUserInput()">Ask</button>
    </div>
</div>

<script>
    // Function to handle user input and display AI response
    function handleUserInput() {
        const userInput = document.getElementById("userInput").value.trim();
        if (userInput === "") return;

        // Display user message
        displayMessage(userInput, "user");

        // Process input and generate AI response
        const aiResponse = getAIResponse(userInput);

        // Display AI message
        setTimeout(() => {
            displayMessage(aiResponse, "ai");
        }, 1000);

        // Clear the input field
        document.getElementById("userInput").value = "";
    }

    // Function to display messages in the chatbox
    function displayMessage(message, sender) {
        const chatbox = document.getElementById("chatbox");
        const div = document.createElement("div");
        div.classList.add(sender === "user" ? "user-msg" : "ai-msg");
        div.textContent = message;
        chatbox.appendChild(div);
        chatbox.scrollTop = chatbox.scrollHeight; // Scroll to bottom
    }

    // Function to simulate AI response based on the user's input
    function getAIResponse(userInput) {
        // Convert the input to lowercase for easy matching
        const input = userInput.toLowerCase();

        // Simple logic to simulate AI responses
        if (input.includes("back pain") || input.includes("lower back")) {
            return "For back pain, you should try gentle stretching, maintaining good posture, and strengthening exercises for the lower back muscles. Applying heat or cold packs may also help.";
        }
        if (input.includes("knee pain")) {
            return "For knee pain, you can try strengthening exercises for the quadriceps and hamstrings. Also, avoid high-impact activities and apply ice if there is swelling.";
        }
        if (input.includes("shoulder pain")) {
            return "For shoulder pain, try gentle shoulder stretches and strengthening exercises. Avoid lifting heavy weights and ensure you have good posture.";
        }
        if (input.includes("neck pain")) {
            return "For neck pain, try gentle neck stretches and heat packs. Ensure you have an ergonomic workstation setup and avoid long periods of neck strain.";
        }
        if (input.includes("sprain") || input.includes("strain")) {
            return "For a sprain or strain, rest the affected area, apply ice, and elevate it. After the initial swelling reduces, gentle stretches can help with recovery.";
        }
        if (input.includes("exercise") || input.includes("workout")) {
            return "Regular exercise like walking, swimming, and yoga can help maintain muscle strength and flexibility, reducing the risk of injury. Always warm up before and cool down after exercise.";
        }

        // Default message for unknown issues
        return "I'm not sure about that. Can you provide more details or describe your symptoms differently?";
    }
</script>

</body>
</html>
