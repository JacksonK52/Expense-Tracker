<script setup>
import Header from '@/components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TransectionHistory from './components/TransectionHistory.vue';
import Transection from './components/Transection.vue';
import '@/assets/style.css';

</script>

<template>
    <Header title="Expense Tracker" by="Jackson Konjengbam" />
    <Balance title="Current Balance" />
    <IncomeExpenses />
    <TransectionHistory />
    <Transection />
</template>

<style scoped>

</style>
