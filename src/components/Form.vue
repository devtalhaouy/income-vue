<template>
  <div>
      <form @submit.prevent="handleSubmit">
          <input type="text" placeholder="description" v-model="data.desc">
          <input type="number" placeholder="price" v-model="data.price">
          <input type="date" placeholder="date" v-model="data.date">
          <button>Add income</button>
      </form>
  </div>
</template>

<script>
import { reactive } from 'vue'
export default {
    name: "Form",
    props:{
        state:Object
    },
    setup(props,{emit}){
        const data = reactive({
            desc: null,
            price: null,
            date: null
        })
        function handleSubmit(){
            emit("add-income",{
                desc: data.desc,
                price: data.price,
                date: data.date,
            });
            data.desc = null
            data.date = null
            data.price = null
        }
        return {
            data,
            handleSubmit
        }
    }
}
</script>

<style scoped>
form{
    display: flex;
    justify-content: center;
    margin-top: 30px;
}
form input{
    color: #000;
    border: none;
    outline: none;
    font-size: 20px;
    padding: 8px;
}
form input::placeholder{
    color: #bbb;
}
form button{
    display: block;
    background: none;
    border: none;
    outline: none;
    color: #fff;
    font-weight: 500;
    text-shadow: 0 1px 2px rgba(0,0,0,0.3);
    padding: 5px 15px;
    background-color: skyblue;
    cursor: pointer;
}
form input:first-of-type,button:first-of-type{
    border-radius: 8px 0px 0px 8px;
}
button:last-of-type{
    border-radius: 0px 8px 8px 0px;
}
</style>>
