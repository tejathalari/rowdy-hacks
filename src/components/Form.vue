<template>
    <div class="container mx-auto py-8 flex justify-center items-center h-screen">
      <div class="text-center">
        <h1 class="text-3xl font-semibold mb-4">Welcome to Our Banking Project</h1>
        <p class="text-lg text-gray-600 mb-8">We're here to simplify your banking experience. Get started by filling out the form below.</p>
  
        <!-- Plus Button -->
        <button @click="toggleFormVisibility" class="bg-blue-500 text-white font-bold py-4 px-8 rounded-full text-4xl mb-8">+</button>
  
        <!-- Form (Initially Hidden) -->
        <div v-if="!loading && showForm" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 w-full max-w-md">
          <h2 class="text-2xl mb-6 text-center font-semibold">Enter Your Details</h2>
          
          <!-- Form Inputs... -->
          <!-- Example Form Inputs -->
          <div class="mb-4">
            <label for="name" class="block text-gray-700 text-sm font-bold mb-2">Name:</label>
            <input type="text" id="name" v-model="formData.name" placeholder="Enter your name" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
          </div>
  
          <div class="mb-4">
            <label for="accountNumber" class="block text-gray-700 text-sm font-bold mb-2">Account Number:</label>
            <input type="text" id="accountNumber" v-model="formData.accountNumber" placeholder="Enter your account number" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
          </div>
  
          <div class="mb-6">
            <label for="confirmAccountNumber" class="block text-gray-700 text-sm font-bold mb-2">Confirm Account Number:</label>
            <input type="text" id="confirmAccountNumber" v-model="formData.confirmAccountNumber" placeholder="Confirm your account number" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
            <p v-if="!isAccountNumberMatch" class="text-red-500 text-xs italic">Account numbers do not match</p>
          </div>
          
          <!-- Submit Button -->
          <div class="flex items-center justify-center">
            <button @click="submitForm"
                    :disabled="!isFormValid || !isAccountNumberMatch"
                    :class="{ 'bg-blue-500 hover:bg-blue-700': isFormValid && isAccountNumberMatch, 'bg-gray-500 cursor-not-allowed': !isFormValid || !isAccountNumberMatch }"
                    class="text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
              Submit
            </button>
          </div>
        </div>
  
        <!-- Spinner (Shown when loading) -->
        <div v-if="loading" class="flex items-center justify-center">
          <img class="spinner animate-delayed-fade-in w-1/6" src="../../src/assets/spinner.gif" alt="Loading Spinner">
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        showForm: false,
        loading: false,
        formData: {
          name: '',
          accountNumber: '',
          confirmAccountNumber: ''
        }
      };
    },
    computed: {
      isFormValid() {
        return this.formData.name && this.formData.accountNumber && this.formData.confirmAccountNumber;
      },
      isAccountNumberMatch() {
        return this.formData.accountNumber === this.formData.confirmAccountNumber;
      }
    },
    methods: {
      toggleFormVisibility() {
        this.showForm = !this.showForm;
      },
      async submitForm() {
        // Show loading spinner
        this.loading = true;
  
        // Simulate form submission delay (replace with actual API call)
        await new Promise(resolve => setTimeout(resolve, 2000));
  
        // Hide form and loading spinner
        this.showForm = false;
        this.loading = false;
  
        // Reset form data
        this.formData = {
          name: '',
          accountNumber: '',
          confirmAccountNumber: ''
        };
      }
    }
  }
  </script>
  
  <style>
  /* Add your custom styles here */
  
  @keyframes delayed-fade-in {
    0% { opacity: 0; } /* Initially invisible */
    100% { opacity: 1; } /* Fully visible after delay */
  }
  
  .animate-delayed-fade-in {
    animation: delayed-fade-in 1s ease; /* Add animation with 1 second delay */
  }
  </style>
  