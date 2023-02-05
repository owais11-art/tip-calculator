<script setup>
    defineProps(['tabs'])
    const emit = defineEmits(['updatePercentageTab'])
    const handleClick = id => emit('updatePercentageTab', id)  
</script>

<template>
    <div class="percentage-tabs">
        <div 
            v-for="tab in tabs"
            :class="{selected: tab.selected, tab: 'tab'}"
            :key="tab.id"
            @click="() => handleClick(tab.id)"
            >{{ tab.percent }}%</div>
    </div>
</template>

<style scoped lang="less">
    .percentage-tabs
    {
        display: flex;
        justify-content: space-around;
        align-items: center;
        background-color: #ece8e8;
        padding: 15px 0;
        flex-wrap: wrap;
        .tab
        {
            font-size: 18px;
            font-weight: 700;
            color: aquamarine;
            background-color: #fff;
            padding: 10px 0;
            border-radius: 8px;
            min-width: 72.41px;
            display: grid;
            place-items: center;
            cursor: pointer;
            &:hover, &.selected{
                color: #fff;
                background-color: aquamarine;
            }
        }
    }
</style>