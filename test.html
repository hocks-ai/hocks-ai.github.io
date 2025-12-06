<script>
  // ⚠️ DO NOT USE API KEY IN FRONTEND
  // সব OpenAI রিকোয়েস্ট যাবে তোমার Cloudflare Worker এ
  const WORKER_API_URL = "https://hocks-ai-backend.test125256.workers.dev/";

  let messageIdCounter = 0;
  let conversationHistory = [];
  let isProcessing = false;

  function createNetworkBackground() {
    const networkBg = document.getElementById('networkBg');
    for (let i = 0; i < 8; i++) {
      const line = document.createElement('div');
      line.className = 'network-line';
      line.style.top = `${Math.random() * 100}%`;
      line.style.width = `${30 + Math.random() * 40}%`;
      line.style.animationDelay = `${Math.random() * 8}s`;
      networkBg.appendChild(line);
    }
    for (let i = 0; i < 15; i++) {
      const particle = document.createElement('div');
      particle.className = 'particle';
      particle.style.left = `${Math.random() * 100}%`;
      particle.style.top = `${Math.random() * 100}%`;
      particle.style.animationDelay = `${Math.random() * 15}s`;
      networkBg.appendChild(particle);
    }
  }

  function showErrorBanner(message) {
    const chatMessages = document.getElementById('chatMessages');
    const errorDiv = document.createElement('div');
    errorDiv.className = 'error-banner';
    errorDiv.innerHTML = `
      <div class="error-banner-icon">⚠️</div>
      <div>${message}</div>
    `;
    chatMessages.appendChild(errorDiv);
    chatMessages.scrollTop = chatMessages.scrollHeight;

    setTimeout(() => errorDiv.remove(), 5000);
  }

  function addMessage(text, isUser = false, isTyping = false) {
    const chatMessages = document.getElementById('chatMessages');
    const messageDiv = document.createElement('div');
    messageDiv.className = `message ${isUser ? 'user' : 'bot'}`;
    messageDiv.dataset.messageId = messageIdCounter++;

    const avatarDiv = document.createElement('div');
    avatarDiv.className = 'message-avatar';

    const bubbleDiv = document.createElement('div');
    bubbleDiv.className = 'message-bubble';

    if (isTyping) {
      const typingIndicator = document.createElement('div');
      typingIndicator.className = 'typing-indicator';
      for (let i = 0; i < 3; i++) {
        const dot = document.createElement('div');
        dot.className = 'typing-dot';
        typingIndicator.appendChild(dot);
      }
      bubbleDiv.appendChild(typingIndicator);
    } else {
      bubbleDiv.textContent = text;
    }

    messageDiv.appendChild(avatarDiv);
    messageDiv.appendChild(bubbleDiv);
    chatMessages.appendChild(messageDiv);
    chatMessages.scrollTop = chatMessages.scrollHeight;

    return messageDiv;
  }

  async function callAI(userMessage) {
    conversationHistory.push({ role: "user", content: userMessage });

    try {
      const response = await fetch(WORKER_API_URL, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          message: userMessage,
          history: conversationHistory
        })
      });

      const data = await response.json();

      const aiResponse =
        data.choices?.[0]?.message?.content ||
        data.response ||
        "I'm here! But I couldn't parse the response.";

      conversationHistory.push({ role: "assistant", content: aiResponse });

      return aiResponse;
    } catch (err) {
      console.error(err);
      return "⚠️ AI server unavailable. Try again.";
    }
  }

  async function handleAIResponse(userMessage) {
    const typingMessage = addMessage("", false, true);

    try {
      const aiResponse = await callAI(userMessage);
      typingMessage.remove();
      addMessage(aiResponse, false);
    } catch (e) {
      typingMessage.remove();
      addMessage("Error occurred!", false);
    }
  }

  async function sendMessage() {
    if (isProcessing) return;

    const chatInput = document.getElementById("chatInput");
    const sendBtn = document.getElementById("sendBtn");
    const message = chatInput.value.trim();

    if (message) {
      isProcessing = true;
      chatInput.disabled = true;
      sendBtn.disabled = true;

      addMessage(message, true);
      chatInput.value = "";

      await handleAIResponse(message);

      isProcessing = false;
      chatInput.disabled = false;
      sendBtn.disabled = false;
      chatInput.focus();
    }
  }

  function initializeChat() {
    createNetworkBackground();
    addMessage("Hello! I’m Hocks AI Assistant. How can I help you today?", false);

    document.getElementById("sendBtn").addEventListener("click", sendMessage);

    document.getElementById("chatInput").addEventListener("keypress", (e) => {
      if (e.key === "Enter" && !isProcessing) {
        sendMessage();
      }
    });

    document.getElementById("chatInput").focus();
  }

  window.addEventListener("DOMContentLoaded", initializeChat);
        </script>
