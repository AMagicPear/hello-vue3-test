<template>
    <div>
      <h1>Message Board</h1>
      <div v-if="messages.length">
        <div v-for="msg in messages" :key="msg.id" class="message">
          {{ msg.text }}
        </div>
      </div>
      <div v-else>
        <p>No messages yet.</p>
      </div>
  
      <input v-model="newMessage" placeholder="Enter your message" />
      <button @click="sendMessage">Send</button>
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  
  export default {
    name: 'MessageBoard',
    setup() {
      const messages = ref([]);
      const newMessage = ref('');
  
      // 获取所有留言
      const loadMessages = async () => {
        try {
          const response = await fetch('http://localhost:3000/messages');
          messages.value = await response.json();
        } catch (error) {
          console.error('Failed to load messages:', error);
        }
      };
  
      // 提交新留言
      const sendMessage = async () => {
        if (!newMessage.value.trim()) return;
  
        try {
          await fetch('http://localhost:3000/messages', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ text: newMessage.value })
          });
          newMessage.value = '';
          await loadMessages();
        } catch (error) {
          console.error('Failed to send message:', error);
        }
      };
  
      onMounted(() => {
        loadMessages();
      });
  
      return { messages, newMessage, sendMessage };
    }
  };
  </script>
  
  <style scoped>
  .message {
    margin: 5px 0;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  </style>