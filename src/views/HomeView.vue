<template>
  <div
    class="flex min-h-screen flex-row"
    :class="{ 'dark-mode': darkMode }">
    <button @click="toggleDarkMode" class="absolute top-4 right-4 p-2 rounded-md bg-indigo-600 text-white">{{ darkMode ? 'Light Mode' : 'Dark Mode' }}</button>
    <div class="left bg-slate-200 flex justify-center" style="width: 40%; align-items: center; display:flexbox">
      <div class="" align="center">
        <img class=" p-2" style="border-radius: 50%; width: 250px; height: 250px;" src="D:\VueProject\PhoneVue\picture\ChriszPic.jpg" alt="">
        <h1 class=" text-black font-serif" style="font-size:xx-large ;">WELCOME TO <span class="text-indigo-600">CHRISZ</span> SHOP</h1>
        <p class=" font-sans text-black" style="font-size:large;">Everything Won't Last Forever</p>
      </div>
    </div>
    <div class="right bg-slate-300" style="width: 60%;">
      <div align="center">
        <h1 class="two" style="margin-top: 10vh; margin-left:20px ; padding: 20px; font-size:x-large; font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;">Smart Choices, Happy Drives: Get More Car for Your Money at <span class="text-indigo-600">CHRISZ</span> SHOP.</h1>
        <p class=" p-8">
        Chrisz Shop: Two Decades of Driving Success Across Borders
        For 20 years, Chrisz Shop has been synonymous with quality car buying, not only in one country, but across two nations with 10 thriving branches. Their journey began in [Year], fueled by the founder's [Founder's name] unwavering passion for making the car buying experience exceptional. <br><br> Chrisz Shop consistently ranks high in customer satisfaction surveys, boasting a loyal clientele who praise their transparent approach, knowledgeable staff, and commitment to fair pricing. <br><br>Through initiatives like [Example: 24/7 customer support, hassle-free returns, community outreach programs], Chrisz Shop has built a strong reputation for prioritizing customer needs and fostering trust. <br><br> Chrisz Shop has been recognized for its excellence by esteemed industry organizations, receiving awards for [Example: best dealership practices, outstanding customer service, innovation in marketing]. These accolades stand as a testament to their dedication to setting high standards. <br><br>Being featured in [Example: national publications, industry reports] has brought Chrisz Shop wider recognition and solidified its position as a respected player in the automotive landscape. </p>
      </div>
    </div>  
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
/* Light mode styles */
.light-mode, .light-mode aside {
  background-color: #ffffff;
  color: #000000;
}

/* Dark mode styles */
.dark-mode, .dark-mode p, .dark-mode h1, .dark-mode .left {
  color: #ffffff;
  background-color: #333333;  
}
.dark-mode .right, .dark-mode .two{
  color: #ffffff;
  background-color: #4b4b4b;
}
.dark-mode .p-8{
  color: #ffffff;
  background-color: #4b4b4b;
}
</style>
