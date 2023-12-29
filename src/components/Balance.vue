<script setup>

const props = defineProps({
    title: {
        type: String,
        required: true
    },
    balance: {
        type: Number,
        default: 0.00
    }
})
</script>

<template>
    <div >
        <h3 class="title">{{ props.title }}</h3>
        <span class="balance"><span class="font-hindi">₹</span>{{ props.balance.toFixed(2) }}</span>
    </div>
</template>

<style scoped>
.title {
    font-weight: 500;
    text-transform: uppercase !important;
    line-height: 0;
}
.balance {
    font-size: 36px;
    font-weight: 500;
}
</style>