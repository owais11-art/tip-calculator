<script setup>
    defineProps(['billTotal'])
</script>

<template>
    <div class="output">
        <div class="tip-amout">
            <div class="label">Tip Amount</div>
            <p class="amount">
                <sup>$</sup>{{ billTotal.tipAmount.toFixed(2) }}
            </p>
        </div>
        <div class="break"></div>
        <div class="total-per-person">
            <div class="label">Total Per Person</div>
            <p class="amount">
                <sup>$</sup>{{ billTotal.totalPerPerson.toFixed(2) }}
            </p>
        </div>
    </div>
</template>

<style scoped lang="less">
    .output
    {
        display: flex;
        flex-direction: column;
        div
        {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 30px;
            padding: 10px 0;
            .amount
            {
                font-size: 50px;
                font-weight: bolder;
            }
            .label
            {
                font-weight: 700;
                font-size: 13px;
            }
        }
        .break
        {
            width: 100%;
            height: 2px;
            padding: 0;
            background-color: #f5f5f5;
        }
    }
</style>