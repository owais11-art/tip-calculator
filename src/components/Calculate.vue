<script setup></script>

<template>
    <div class="calculate">
        <button @click="$emit('calculate')">Calculate</button>
    </div>
</template>

<style scoped lang="less">
    .calculate
    {
        width: 100%;
        padding: 20px 10px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        button
        {
            padding: 10px 60px;
            color: #fff;
            background-color: rgb(240, 93, 40);
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 18px;
            font-family: 'Roboto Mono', monospace;
        }
    }
</style>