<template>
    <div class="bg-white shadow-md rounded-lg p-4 cursor-pointer transition-all duration-300" 
         :class="{ 'border-blue-500 border-2': expanded }"
         @click="toggleExpanded">
      <div class="card-content">
        <h2 class="text-lg font-semibold">{{ data.title }}</h2>
        <p class="text-gray-600">{{ data.description }}</p>
      </div>
      <div class="card-actions" v-if="expanded">
        <button class="bg-green-500 text-white px-4 py-2 rounded-md ml-32" @click="accept">Accept</button>
        <button class="bg-red-500 text-white px-4 py-2 ml-10 rounded-md ml-32" @click="ignore">Ignore</button>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    props: {
      data: Object
    },
    data() {
      return {
        expanded: false
      };
    },
    methods: {
      toggleExpanded() {
        this.expanded = !this.expanded;
      },
      async accept() {
        console.log("Accepted");
        try {
          // Send request to your backend server to handle email sending
          await axios.post('YOUR_BACKEND_API_ENDPOINT/send-email', {
            to: 'bhavanakondeti2000@gmail.com', // Replace with recipient's email
            from: 'tsteja1999@gmail.com', // Replace with sender's email
            subject: 'Accepted Invitation',
            text: 'Your invitation has been accepted.'
          });
          console.log('Email sent successfully');
        } catch (error) {
          console.error('Error sending email:', error);
        }
      },
      ignore() {
        // Handle ignore action
      }
    }
  }
  </script>
  