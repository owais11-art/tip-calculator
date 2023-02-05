<script setup>
    defineProps(['billDetails'])
    const emit = defineEmits(['updateBillDetails'])
    const handleInput = (event, updateProperty) => {
        const payload = {
            value : Number.isNaN(parseFloat(event.target.textContent)) ? 0 : parseFloat(event.target.textContent),
            updateProperty
        }
        emit('updateBillDetails', payload)
    }
</script>

<template>
    <div class="input">
        <div class="bill-amount">
            <div 
                class="number" 
                contenteditable="true"
                @input="e => handleInput(e, 'amount')"
                >{{ billDetails.amount }}</div>
            <div class="break"></div>
            <div class="label">Bill Amount</div>
        </div>
        <div class="v-break"></div>
        <div class="number-of-people">
            <div 
                class="number" 
                contenteditable="true"
                @input="e => handleInput(e, 'people')"
                >{{ billDetails.people }}</div>
            <div class="break"></div>
            <div class="label">Number of People</div>
        </div>
    </div>
</template>

<style scoped lang="less">
    .input
    {
        display: flex;
        justify-content: space-around;
        gap: 30px;
        background-color: aliceblue;
        padding: 0 10px;
        @media(max-width: 500px){
            flex-direction: column;
            gap: 10px;
        }
        div
        {
            display: flex;
            flex-direction: column;
            gap: 5px;
            text-align: center;
            padding: 10px 0;
            .break
            {
                width: 100%;
                border-top: 3px dotted #ece8e8;
            }
            .number
            {
                font-size: 32px;
                font-weight: bolder;
                border: none;
                outline: none;
            }
            .label
            {
                font-size: 13px;
                font-weight: 700;
            }
        }
        .bill-amount
        {
            flex-grow: 5;
            @media(max-width: 500px){
                flex-grow: 1;
            }
        }
        .number-of-people
        {
            flex-grow: 1;
        }
        .v-break
        {
            display: block;
            align-self: stretch;
            border-left: 3px solid #ece8e8;
            padding: 0;
            @media(max-width: 500px){
                display: none;
            }
        }
    }
</style>