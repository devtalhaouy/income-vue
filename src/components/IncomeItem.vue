<template>
  <div class="income-item">
      <div class="removeItem" @click="deleteIncome">x</div>
      <div class="desc">{{income.desc}}</div>
      <div class="price">{{income.price}}</div>
      <div class="date">{{formated}}</div>
  </div>
</template>

<script>
export default {
    name: "IncomeItem",
    props:{
        income:Object
    },
    setup(props,{emit}){
        let date = new Date(props.income.date)
        let day = date.getDate()
        let month = date.getMonth()
        let year = date.getFullYear()
        let formated = day + "/"+month+ "/"+year

        function deleteIncome(){
            emit("delete-income",props.income.id)
        }
        return{
            formated,
            deleteIncome
        }
    }
}
</script>

<style scoped>
.income-item{
    position: relative;
    display: flex;
    padding: 15px 15px 15px 0;
    background-color: #fff;
    border-radius: 8px;
    max-width: 600px;
    margin: 10px auto 30px;
}
.removeItem{
    color: red;
    font-weight: 600;
    font-size: 20px;
    line-height: 1;
    text-align: center;
    margin: 0 15px;
    cursor: pointer;
}
.desc{
    color: #666;
    flex: 1 1 100%;
    font-size: 20px;
}
.price{
    color: #666;
    min-width: 100px;
    font-size: 20px;
}
.date{
    color: #666;
    text-align: right;
    font-size: 20px;
}
</style>