<script setup>

const props = defineProps({
    income: {
        type: Number,
        default: 0.00
    },
    expenses: {
        type: Number,
        default: 0.00
    }
})
</script>

<template>
    <div class="incomeExpenses shadow mb-2">
        <!-- Income -->
        <div class="py-2 border-right">
            <p class="title">Income</p>
            <p class="total text-primary">
                <span class="font-hindi">₹</span>{{ props.income.toFixed(2) }}
            </p>
        </div>

        <!-- Expenditure -->
        <div class="py-2">
            <p class="title">Expenses</p>
            <p class="total text-danger">
                <span class="font-hindi">₹</span>{{ props.expenses.toFixed(2) }}
            </p>
        </div>
    </div>
</template>

<style scoped>
.incomeExpenses {
    background-color: var(--white);
    display: flex;
    justify-content: space-around;
    text-align: center;
}

.title {
    width: 130px;
    font-size: 16px;
    letter-spacing: 1.5px;
    font-weight: 500;
    text-transform: uppercase;
    text-decoration: underline;
}

.total {
    font-size: 24px;
    font-weight: 500;
}
</style>