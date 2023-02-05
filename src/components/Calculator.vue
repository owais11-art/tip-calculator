<script setup>
    import Output from './Output.vue'
    import Input from './Input.vue'
    import PercentageTabs from './PercentageTabs.vue'
    import Calculate from './Calculate.vue'
    import { ref } from 'vue';
    const billDetails = ref({
        amount: 0,
        people: 0
    })
    const billTotal = ref({
        tipAmount: 0,
        totalPerPerson: 0
    })
    const tabs = ref([
        {
            id: 1,
            percent: 5,
            selected: false
        },
        {
            id: 2,
            percent: 10,
            selected: false
        },
        {
            id: 3,
            percent: 15,
            selected: true
        },
        {
            id: 4,
            percent: 20,
            selected: false
        }
    ])
    const updateBillDetails = ({value, updateProperty}) => {
        for (const key in billDetails.value){
            if(key === updateProperty) billDetails.value[key] = value
        }
    }
    const updatePercentageTab = id => {
        tabs.value = tabs.value
                        .map(tab => tab.selected ? {...tab, selected: false} : tab)
                        .map(tab => tab.id === id ? {...tab, selected: true} : tab)
    }
    const calculate = () => {
        const {amount, people} = billDetails.value
        const tipPercentage = tabs.value.find(tab => tab.selected).percent
        billTotal.value.tipAmount = (tipPercentage / 100) * amount
        billTotal.value.totalPerPerson = (amount + billTotal.value.tipAmount) / people
    }
</script>

<template>
    <main class="calculator">
        <Output
            :billTotal="billTotal"
        />
        <Input
            :billDetails="billDetails"
            @updateBillDetails="updateBillDetails"
        />
        <PercentageTabs
            :tabs="tabs"
            @updatePercentageTab="updatePercentageTab"
        />
        <Calculate
            @calculate="calculate"
        />
    </main>
</template>

<style scoped lang="less">
    .calculator
    {
        width: 500px;
        background-color: #fff;
        border-radius: 6px;
        padding-top: 20px;
        @media(max-width: 500px){
            width: 100%;
        }
    }
</style>