<template>
    <div>
        <Header :totalIncome="state.totalIncome"/>
        <Form :state="state" @add-income="addIncome"/>
        <IncomeItem @delete-income="deleteIncome" v-for="item in state.income" :key="item.id" :income="item"/>
    </div>
</template>

<script>
import { computed, reactive } from 'vue'
import Form from './Form.vue'
import Header from './Header.vue'
import IncomeItem from './IncomeItem.vue'
export default{
    name: "Income",
    setup(){
        const state = reactive({
            income: [
                {
                desc: "vuejs and typescript",
                price: 200,
                date: new Date()
                },
                {
                desc: "angular and typescript",
                price: 379,
                date: new Date()
            },
            ],
            totalIncome: computed(()=>{
                let temp = 0
                if(state.income.length >0){
                  for(var i = 0;i< state.income.length;i++){
                      temp = state.income[i].price
                  }
                }
                return temp;
            })
        })
        function addIncome(data){
            const d = data.date.split('-');
            const newd = new Date(d[0],d[1],d[2]);
            state.income = [...state.income,{
                id: Date.now(),
                desc: data.desc,
                price: data.price,
                date: newd.getTime()
            }];
            console.log(state.income);
        }
        function deleteIncome(id){
            state.income = state.income.filter((item)=>item.id!==id);
        }
        return{
            Header,
            Form,
            state,
            addIncome,
            IncomeItem,
            deleteIncome
        }
    }

}
</script>

<style lang="scss" scoped>

</style>