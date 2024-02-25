<template>
  <header class="bg-gray-700 text-white shadow-lg">
    <div class="container mx-auto flex justify-between items-center py-4">
      <!-- Logo -->
      <div class="flex items-center">
        <!-- <img src="logo.png" alt="Logo" class="h-10 mr-2"> -->
        <h1 class="text-xl font-semibold">Banking Portal</h1>
      </div>
      
      <!-- Navigation Menu -->
      <nav>
        <ul class="flex space-x-4">
          <li><a href="#" class="hover:text-gray-300">Home</a></li>
          <li><a href="#" class="hover:text-gray-300">Services</a></li>
          <li><a href="#" class="hover:text-gray-300">About</a></li>
          <li><a href="#" class="hover:text-gray-300">Contact</a></li>
        </ul>
      </nav>
      
      <!-- User Profile (Example) -->
      <div class="flex items-center space-x-4">
        <div class="flex items-center">
          <!-- <img src="user-avatar.png" alt="User Avatar" class="h-8 w-8 rounded-full"> -->
          <span class="font-semibold">John Doe</span>
        </div>
        <button class="bg-white text-gray-700 font-semibold py-2 px-4 rounded-full">Logout</button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  // Add your script logic here
}
</script>

<style>
/* Add your custom styles here */
</style>
