<script setup>
import Header from '@/components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TransectionHistory from './components/TransectionHistory.vue';
import Transection from './components/Transection.vue';
import '@/assets/style.css';
import { ref, computed, onMounted } from 'vue';
import { useToast } from 'vue-toastification';

const toast = useToast();

const transactions = ref([]);

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

    saveTransactionsToLocalStorage();

    toast.success('New Transaction Added!');
}

// Generate Unique Id
const generateUniqueId = () => {
    return Math.floor(Math.random() * 100000);
}

// Delete Transaction
const handleTransactionDeleted = (id) => {
    transactions.value = transactions.value.filter((transaction) => transaction.id !== id);

    saveTransactionsToLocalStorage();

    toast.success('Transaction Deleted!');
}

// Save to localStorage
const saveTransactionsToLocalStorage = () => {
    localStorage.setItem('transactions', JSON.stringify(transactions.value));
}

// On Mounted
onMounted(() => {
    const savedTransactions = JSON.parse(localStorage.getItem('transactions'));

    if(savedTransactions) {
        transactions.value = savedTransactions;
    }
})
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
