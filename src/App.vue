<template>
  <div
    class="flex min-h-screen flex-row"
    :class="{ 'dark-mode': darkMode }"
  >
    <aside class="sidebar w-48 -translate-x-full transform bg-white p-4 transition-transform duration-150 ease-in md:translate-x-0 md:shadow-md">
      <div class="my-4 w-full border-b-4 border-indigo-100 text-center">
        <span class="font-mono text-xl font-bold tracking-widest">
          <span class="text-indigo-600">CHRISZ</span> SHOP
        </span>
      </div>
      <br /><br />
      <div class="my-4">
        <nav>
          <RouterLink to="/" class="p-2 rounded-sm hover:bg-stone-200">Home</RouterLink><br /><br /><br />
          <RouterLink to="/CarShop" class="p-2 rounded-sm hover:bg-stone-200">CarShop</RouterLink><br /><br /><br />
          <RouterLink to="/Moto" class="p-2 rounded-sm hover:bg-stone-200">MotoShop</RouterLink><br /><br /><br />
          <RouterLink to="/about" class="p-2 rounded-sm hover:bg-stone-200">About</RouterLink><br /><br /><br />
        </nav>
      </div>
    </aside>

    <main class="main -ml-48 flex flex-grow flex-col p-4 transition-all duration-150 ease-in md:ml-0">
      <div class="">
        <RouterView />
      </div>
    </main>

    <!-- Dark Mode / Light Mode Switch Button -->
    <!-- <button @click="toggleDarkMode" class="absolute top-4 right-4 p-2 rounded-md bg-indigo-600 text-white">Toggle Dark Mode</button> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      darkMode: false,
    };
  },
  methods: {
    toggleDarkMode() {
      this.darkMode = !this.darkMode;
    },
  },
};
</script>

<style scoped>
 Light mode styles
.light-mode, aside {
  background-color: #ffffff;
  color: #000000;
}

/* Dark mode styles */
.dark-mode {
  color: black;
  background-color: #333333;  
}

</style>
