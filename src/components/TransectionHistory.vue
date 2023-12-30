<script setup>

const props = defineProps({
    transactions: {
        type: Object,
        required: true
    }
});

const emits = defineEmits(['transactionDeleted']);

const handleDelete = (id) => {
    emits('transactionDeleted', id);
}
</script>

<template>
    <div class="mb-2">
        <h3 class="title">History</h3>
        <hr>
        <ul class="unorder-list">
            <li 
                class="list"
                v-for="transaction in props.transactions"
                    :key="transaction.id"
            >
                <div class="item" :class="transaction.amount > 0 ? 'plus' : 'minus'">
                    <p>{{ transaction.remark }}</p>
                    <p><span class="font-hindi">₹</span> {{ transaction.amount }}</p>
                </div>
                <button @click="handleDelete(transaction.id)" class="btn-delete">X</button>
            </li>
        </ul>
    </div>
</template>

<style scoped>
.title {
    font-size: 24px;
    font-weight: 500;
}

.list {
    margin-top: 2px;
    padding: 5px 10px;
    /* background-color: var(--white); */
    list-style-type: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.list:hover .btn-delete {
    opacity: 1;
}

.minus {
    border-left: 5px solid var(--danger);
}

.plus {
    border-left: 5px solid var(--success);
}

.item {
    width: 100%;
    padding: 0 5px;
    display: flex;
    justify-content: space-between;
    background-color: var(--white);
}

.btn-delete {
    margin: 0 5px;
    padding: 3px 8px;
    font-size: 14px;
    font-weight: 600;
    border: none;
    border-radius: 5px;
    background-color: var(--danger);
    color: var(--white);
    opacity: 0;
}
</style>