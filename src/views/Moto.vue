<template>
    <div class="moto">
        <div :class="{ 'dark-mode': darkMode }">
            <button @click="toggleDarkMode" class="absolute top-4 right-4 p-2 rounded-md bg-indigo-600 text-white">{{
                darkMode ? 'Light Mode' : 'Dark Mode' }}</button>

            <section class="header">
                <header class="bg-purple-800 text-white p-4 text-center font-serif"
                    style="border-radius: 15px; font-size: xx-large;">Moto</header>
            </section>
            <br>
            <section class="content">
                <div class="moto-list">
                    <!-- moto Selling List -->
                    <div v-for="(moto, index) in data" :key="index" class="moto-item">
                        <img :src="moto.img" alt="moto Image" class="rounded-lg">
                        <div class="details rounded-lg bg-gray-200 p-2">
                            <div>{{ moto.Name }}</div>
                            <div>Year: {{ moto.year }}</div>
                            <div>Price: ${{ moto.price }}</div>
                            <div class="button-container">
                                <button @click="buymoto(moto)" class="btn-buy">Buy</button>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- Selected Items -->
                <div class="selected-items">
                    <div v-for="(item, index) in selectedItems" :key="index">
                        <img :src="item.img" alt="moto Image" class="rounded-lg">
                        <div class="details rounded-lg bg-gray-200 p-2">
                            <div>{{ item.Name }}</div>
                            <div>Year: {{ item.year }}</div>
                            <div>Price: ${{ item.price * item.quantity }}</div>

                            <div class="button-container">
                                <button @click="decreaseQuantity(index)" class="btn-">-</button>
                                <span> {{ item.quantity }} </span>
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
                { img: "/picture/HondaDream.jpg", Name: "Honda Dream", year: 2020, price: 100000 },
                { img: "/picture/HondaClick.jpg", Name: "Honda Click", year: 2021, price: 150000 },
                { img: "/picture/CalypsoOri.jpg", Name: "Calypso Ori", year: 2022, price: 200000 },
                { img: "/picture/CalypsoXplorer.jpg", Name: "Calypso Xplorer", year: 2020, price: 11000 },
                { img: "/picture/HondaPCX.jpg", Name: "Honda PCX", year: 2021, price: 12000 },
                { img: "/picture/Kawasuki.jpg", Name: "Kawasuki", year: 2022, price: 130000 },
                { img: "/picture/Yamaha.jpg", Name: "Yamaha", year: 2020, price: 90000 },
                { img: "/picture/Ducati.jpg", Name: "Ducati", year: 2021, price: 18000 },
                { img: "/picture/Susuki.jpg", Name: "Susuki", year: 2022, price: 22000 },
                { img: "/picture/Susuki.png", Name: "Susuki", year: 2020, price: 9500 }
            ],
            darkMode: false,
            selectedItems: [],
            totalPrice: 0
        };
    },
    methods: {
        //   ...mapMutations(['addSelectedItems']),
        // confirmPurchase() {
        //   if (this.selectedItems.length > 0) {
        //     const confirmation = confirm("Are you sure you want to confirm the purchase?");
        //     if (confirmation) {
        //       // Dispatch action to Vuex store
        //       this.addSelectedItems(this.selectedItems);
        //       this.clearAll();
        //     }
        //   } else {
        //     alert("No items selected for purchase.");
        //   }
        // },
        buymoto(moto) {
            const selectedItemIndex = this.selectedItems.findIndex(item => item.Name === moto.Name && item.year === moto.year);
            if (selectedItemIndex !== -1) {
                this.selectedItems[selectedItemIndex].quantity++;
            } else {
                this.selectedItems.push({ ...moto, quantity: 1 });
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

.moto-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    flex: 1;
    padding: 0 10px;
}

.moto-item {
    margin-bottom: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    flex: 0 0 calc(30% - 20px);
    /* Adjust based on the number of items you want per row */
}

.selected-items {
    border: 1px solid #ccc;
    padding: 10px;
    flex: 0 0 calc(30% - 20px);
    /* Adjust based on the number of items you want per row */
}

.selected-items>div {
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
    margin-top: auto;
    /* Pushes the button to the bottom */
    display: flex;
    justify-content: center;
    /* Centers the button horizontally */
}

.button-container1 {
    margin-top: auto;
    /* Pushes the button to the bottom */
    display: flex;
    justify-content: right;
    /* right the button horizontally */
}

.btn-buy {
    padding: 8px 16px;
    /* Adjust padding as needed */
    background-color: #4CAF50;
    /* Green background color */
    color: white;
    /* Text color */
    border: none;
    /* Remove default button border */
    border-radius: 4px;
    /* Add border radius for rounded corners */
    cursor: Hand;
    /* Change cursor on hover */
}

.btn-buy:hover {
    background-color: #45a049;
    /* Darker green color on hover */
}

.btn- {
    padding: 4px 12px;
    /* Adjust padding as needed */
    background-color: #af4c4c;
    /* Green background color */
    color: white;
    /* Text color */
    border: none;
    /* Remove default button border */
    border-radius: 4px;
    /* Add border radius for rounded corners */
    cursor: hand;
    /* Change cursor on hover */
}

.btnPlus {
    padding: 4px 10px;
    /* Adjust padding as needed */
    background-color: #4CAF50;
    /* Green background color */
    color: white;
    /* Text color */
    border: none;
    /* Remove default button border */
    border-radius: 4px;
    /* Add border radius for rounded corners */
    cursor: hand;
    /* Change cursor on hover */
}

.confirm {
    padding: 4px 10px;
    /* Adjust padding as needed */
    background-color: #4CAF50;
    /* Green background color */
    color: white;
    /* Text color */
    border: none;
    /* Remove default button border */
    border-radius: 4px;
    /* Add border radius for rounded corners */
    cursor: hand;
    /* Change cursor on hover */
}

.clear {
    padding: 4px 10px;
    /* Adjust padding as needed */
    background-color: #af4c4c;
    /* Green background color */
    color: white;
    /* Text color */
    border: none;
    /* Remove default button border */
    border-radius: 4px;
    /* Add border radius for rounded corners */
    cursor: hand;
    /* Change cursor on hover */
}

/* Light mode styles */
.light-mode,
.light-mode aside {
    background-color: #ffffff;
    color: #000000;
}

/* Dark mode styles */
.dark-mode,
.dark-mode {
    color: black;
    background-color: #333333;
}</style>