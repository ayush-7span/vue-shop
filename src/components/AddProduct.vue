<template>
    <div class="add-product">
        <form @submit.prevent="onsubmit">
            <input type="text" placeholder="add product" v-model="title"/>
            <input type="text" placeholder="add price" v-model="price"/>
            <input type="submit" value="submit"/>
        </form>
    </div>
  </template>
  <script>
  import { mapActions } from 'vuex';
  export default {
    name:"AddProduct",
    data(){
        return{
            title:"",
            price:""
        };
    },
    methods:{
        ...mapActions(["addProduct"]),
        onsubmit(){
            this.addProduct({
                title:this.title,
                price:this.price
            })

        }
    }
  }
  </script>
  <style scoped>
.add-product {
  background: #fff;
  padding: 15px;
  border-radius: 5px;
  margin-bottom: 20px;
}
form {
  display: flex;
  justify-content: space-between;
}
input[type="text"] {
  width: 270px;
  padding: 10px;
  border: 1px solid #2c3e50;
  outline: 0;
}
input[type="submit"] {
  width: 120px;
  background: #2c3e50;
  color: #fff;
  border: 1px #2c3e50 solid;
  cursor: pointer;
}
  </style>
  