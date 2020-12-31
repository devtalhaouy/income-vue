<template>
  <header>
      <h1>Income Tracker</h1>
      <div class="total">$ {{ totalIncome }}</div>
  </header>
</template>

<script>
export default {
    name: "Header",
    props:{
        totalIncome: Number
    }
   
}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 30px;
    background-color: rgb(43, 45, 46);
    border-bottom: 5px solid skyblue;
}
header h1{
    color: #fff;
    font-size: 28px;
}
header .total{
    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    background-color:skyblue;
    color: #fff;
    font-size: 20px;
    font-weight: bold;
    padding: 6px 10px;
    min-width: 100px;
    text-align: center;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.3);

    
}
</style>