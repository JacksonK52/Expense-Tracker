<script setup>
import Header from '@/components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TransectionHistory from './components/TransectionHistory.vue';
import Transection from './components/Transection.vue';
import '@/assets/style.css';
import { ref, computed } from 'vue';
import { useToast } from 'vue-toastification';

const toast = useToast();

const transactions = ref([
    { id: 1, remark: 'Salaray', amount: 30000 },
    { id: 2, remark: 'Utilities', amount: -10000 },
    { id: 3, remark: 'Food', amount: -100 }
]);

// Calculate total
const total = computed(() => {
    return transactions.value.reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0)
});

// Calculate income
const income = computed(() => {
    return transactions.value
        .filter((transaction) => transaction.amount > 0)
        .reduce((acc, transaction) => {
            return acc + transaction.amount
        }, 0)
})

// Calculate expenses
const expenses = computed(() => {
    return transactions.value
        .filter((transaction) => transaction.amount < 0)
        .reduce((acc, transaction) => {
            return acc + transaction.amount
        }, 0)
})

// Add Transaction
const handleTransactionSubmitted = (transactionData) => {
    transactions.value.push({
        id: generateUniqueId(),
        remark: transactionData.remark,
        amount: transactionData.amount
    });

    toast.success('New Transaction Added!');
}

// Generate Unique Id
const generateUniqueId = () => {
    return Math.floor(Math.random() * 100000);
}

// Delete Transaction
const handleTransactionDeleted = (id) => {
    console.log(id);
    // transactions.value.splice(id, 1);
}
</script>

<template>
    <div class="container">
        <Header title="Expense Tracker" by="Jackson Konjengbam" />
        <Balance title="Current Balance" :balance="total" />
        <IncomeExpenses :income="income" :expenses="Math.abs(expenses)" />
        <TransectionHistory :transactions="transactions" @transactionDeleted="handleTransactionDeleted" />
        <Transection @transactionSubmitted="handleTransactionSubmitted" />
    </div>
</template>

<style scoped>

</style>
