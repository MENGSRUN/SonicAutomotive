<template>
    <div class="container-1">
        <video  class="video">
            <source src="../assets/car/Ford.mp4" type="video/mp4">
        </video>
    </div>
    <br>
    <div class="container ">
       

       <div class="row row-col-4">
           <div class="card" style="width: 18rem; margin-top: 20px;" v-for="item in Carlist" :key="item.id">
               <img :src="item.ImageCar" alt="..." height="144" style="padding-top: 13px;">
               <div class="card-body">
                   <h5 class="card-title">{{ item.Brand }}</h5>

                   <p class="card-text">{{ item.Model }}</p>
                   <div class="row row-cols-2 "><router-link :to="'/Buy'  + '/' + item.id"><a href="#" class="btn" style="background-color: rgb(245, 88, 12); "><i
                                class="fa-solid fa-basket-shopping"></i> Buy</a></router-link>
                       <router-link :to="'/' + item.Brand + '/' + item.id"><a href="#" class="btn btn-primary"><i
                                   class="fa-solid fa-circle-info"></i> Info</a> </router-link>
                   </div>

               </div>
               <div class="card-footer">
                   <small class="text" style="color: whitesmoke ;">{{ item.Price }} $</small>
               </div>
           </div>
       </div>
   </div>
   <br />
</template>
<script>
import axios from "axios";

export default {
    name: "CarTable",
    data() {
        return {
            Carlist: [],
        };
    },

    created() {
        this.getProducts();
    },

    methods: {
        // Get All Products
        async getProducts() {
            try {
                const response = await axios.get("http://localhost:5000/products/Ford");
                this.Carlist = response.data;
            } catch (err) {
                console.log(err);
            }
        },



    },
};
</script>
<style scoped>
.container-1{
    background:url("https://images6.alphacoders.com/107/1078863.jpg") center fixed no-repeat;
   background-size: 100%;

    
}

.video{
    width: 1010px;
    
}
.row{
    justify-content: space-between;
}
.card{
    background-color: rgb(63, 63, 63);
    color: beige;
}
a:hover{
    color: white;
}
</style>