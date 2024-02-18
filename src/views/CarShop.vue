<template>
    <div class="ca">
      <div :class="{ 'dark-mode': darkMode }">
    <button @click="toggleDarkMode" class="absolute top-4 right-4 p-2 rounded-md bg-indigo-600 text-white">{{ darkMode ? 'Light Mode' : 'Dark Mode' }}</button>

      <section class="header">
        <header class="bg-purple-800 text-white p-4 text-center font-serif" style="border-radius: 15px; font-size:xx-large;">Car</header>
      </section>
      <br>
      <section class="content">
        <div class="car-list">
          <!-- Car Selling List -->
          <div v-for="(car, index) in data" :key="index" class="car-item">
            <img :src="car.img" alt="Car Image" class="rounded-lg">
            <div class="details rounded-lg bg-gray-200 p-2">
              <div>{{ car.Name }}</div>
              <div>Year: {{ car.year }}</div>
              <div>Price: ${{ car.price }}</div>
              <div class="button-container">
                <button @click="buyCar(car)" class="btn-buy">Buy</button>
              </div>
            </div>
          </div>
        </div>
        <!-- Selected Items -->
        <div class="selected-items">
          <div v-for="(item, index) in selectedItems" :key="index">
            <img :src="item.img" alt="Car Image" class="rounded-lg">
            <div class="details rounded-lg bg-gray-200 p-2">
              <div>{{ item.Name }}</div>
              <div>Year: {{ item.year }}</div>
              <div>Price: ${{ item.price * item.quantity }}</div>
              
              <div class="button-container">
                <button @click="decreaseQuantity(index)" class="btn-">-</button>
                <span>  {{ item.quantity }}  </span>
                <button @click="increaseQuantity(index)" class="btnPlus">+</button>  
              </div>
              <button @click="cancelItem(index)" style="padding: 10px;">Cancel</button>
            </div>
          </div>
          <div class="total-price " style="color: rgb(172, 126, 10);">Total Price: ${{ totalPrice }}</div>
          <div class="button-container ">
            <button @click="confirmPurchase" class="confirm ">Confirm Purchase</button>
          </div>
          <div class="button-container1">
            <button @click="clearAll" class="clear">Clear All</button>
          </div>
          

          
        </div>
      </section>
    </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        data: [
            { img: "/picture/NissanGTR.jpg", Name: "Nissan", year: 2020, price: 100000 },
            { img: "/picture/NissanGTR.jpg", Name: "Nissan", year: 2021, price: 150000 },
            { img: "/picture/BMW7.jpg", Name: "BMW", year: 2022, price: 20000 },
            { img: "/picture/Farrari.jpg", Name: "Ferrari", year: 2020, price: 11000 },
            { img: "/picture/Farrari.jpg", Name: "Ferrari", year: 2021, price: 12000 },
            { img: "/picture/Toyota.jpg", Name: "Toyota", year: 2022, price: 13000 },
            { img: "/picture/Toyota.jpg", Name: "Toyota", year: 2020, price: 90000 },
            { img: "/picture/FordRapter.jpg", Name: "Ford", year: 2021, price: 18000 },
            { img: "/picture/FordRapter.jpg", Name: "Ford", year: 2022, price: 220000 },
            { img: "/picture/Camry.png", Name: "Camry", year: 2020, price: 95000 }
            ],
        darkMode: false,
        selectedItems: [],
        totalPrice: 0
      };
    },
    methods: {
      buyCar(car) {
        const selectedItemIndex = this.selectedItems.findIndex(item => item.Name === car.Name && item.year === car.year);
        if (selectedItemIndex !== -1) {
          this.selectedItems[selectedItemIndex].quantity++;
        } else {
          this.selectedItems.push({ ...car, quantity: 1 });
        }
        this.calculateTotalPrice();
      },
      toggleDarkMode() {
      this.darkMode = !this.darkMode;
    },
      increaseQuantity(index) {
        this.selectedItems[index].quantity++;
        this.calculateTotalPrice();
      },
      decreaseQuantity(index) {
        if (this.selectedItems[index].quantity > 1) {
          this.selectedItems[index].quantity--;
          this.calculateTotalPrice();
        } else {
          this.selectedItems.splice(index, 1);
          this.calculateTotalPrice();
        }
      },
      cancelItem(index) {
        const cancelledItem = this.selectedItems[index];
        this.totalPrice -= cancelledItem.price * cancelledItem.quantity;
        this.selectedItems.splice(index, 1);
      },
      confirmPurchase() {
        if (this.selectedItems.length > 0) {
          const confirmation = confirm("Are you sure you want to confirm the purchase?");
          if (confirmation) {
            this.clearAll();
          }
        } else {
          alert("No items selected for purchase.");
        }
      },
      clearAll() {
        this.selectedItems = [];
        this.totalPrice = 0;
      },
      calculateTotalPrice() {
        this.totalPrice = this.selectedItems.reduce((total, item) => total + (item.price * item.quantity), 0);
      }
    }
  };
  </script>
  
  <style scoped>
  /* Add your custom CSS styles here */
  .phone {
    display: flex;
    flex-direction: column;
  }
  
  .header {
    width: 100%;
    border-radius: 15px;
    background: linear-gradient(to right, #8B008B, #4B0082);
  }
  
  .content {
    display: flex;
    flex: 1;
    width: 100%;
  }
  
  .car-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    flex: 1;
    padding: 0 10px;
  }
  
  .car-item {
    margin-bottom: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    flex: 0 0 calc(30% - 20px); /* Adjust based on the number of items you want per row */
  }
  
  .selected-items {
    border: 1px solid #ccc;
    padding: 10px;
    flex: 0 0 calc(30% - 20px); /* Adjust based on the number of items you want per row */
  }
  
  .selected-items > div {
    margin-bottom: 10px;
  }
  
  .total-price {
    margin-top: 10px;
  }
  
  .rounded-lg {
    border-radius: 8px;
  }
  .details {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.button-container {
  margin-top: auto; /* Pushes the button to the bottom */
  display: flex;
  justify-content: center; /* Centers the button horizontally */
}
.button-container1 {
  margin-top: auto; /* Pushes the button to the bottom */
  display: flex;
  justify-content: right; /* right the button horizontally */
}
.btn-buy {
  padding: 8px 16px; /* Adjust padding as needed */
  background-color: #4CAF50; /* Green background color */
  color: white; /* Text color */
  border: none; /* Remove default button border */
  border-radius: 4px; /* Add border radius for rounded corners */
  cursor: Hand; /* Change cursor on hover */
}

.btn-buy:hover {
  background-color: #45a049; /* Darker green color on hover */
}
.btn-{
  padding: 4px 12px; /* Adjust padding as needed */
  background-color: #af4c4c; /* Green background color */
  color: white; /* Text color */
  border: none; /* Remove default button border */
  border-radius: 4px; /* Add border radius for rounded corners */
  cursor: hand; /* Change cursor on hover */
}
  .btnPlus{
  padding: 4px 10px; /* Adjust padding as needed */
  background-color: #4CAF50; /* Green background color */
  color: white; /* Text color */
  border: none; /* Remove default button border */
  border-radius: 4px; /* Add border radius for rounded corners */
  cursor: hand; /* Change cursor on hover */
}
.confirm{
  padding: 4px 10px; /* Adjust padding as needed */
  background-color: #4CAF50; /* Green background color */
  color: white; /* Text color */
  border: none; /* Remove default button border */
  border-radius: 4px; /* Add border radius for rounded corners */
  cursor: hand; /* Change cursor on hover */
}
.clear{
  padding: 4px 10px; /* Adjust padding as needed */
  background-color: #af4c4c; /* Green background color */
  color: white; /* Text color */
  border: none; /* Remove default button border */
  border-radius: 4px; /* Add border radius for rounded corners */
  cursor: hand; /* Change cursor on hover */
}
/* Light mode styles */
.light-mode, .light-mode aside {
  background-color: #ffffff;
  color: #000000;
}

/* Dark mode styles */
.dark-mode, .dark-mode  {
  color: black;
  background-color: #333333;  
}
</style>
  