<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const remark = ref('');
const amount = ref('');

const toast = useToast();

const emit = defineEmits(['transactionSubmitted']);

const handleSubmit = () => {
    if(!remark.value || !amount.value) {
        toast.error('Both fields must be filled!');
        return;
    }

    emit('transactionSubmitted', {
        remark: remark.value,
        amount: parseFloat(amount.value)
    })

    remark.value = '';
    amount.value = '';
}
</script>

<template>
    <div>
        <h3 class="title">New Transaction</h3>
        <hr>
        <form @submit.prevent="handleSubmit">
            <div class="form-group">
                <label for="remark">Remark</label>
                <input type="text" class="form-control" name="remark" id="remark" v-model="remark" placeholder="Chai and Biscuits" autofocus>
            </div>
            <div class="form-group">
                <label for="amount">Amount</label>
                <input type="text" class="form-control" name="amount" id="amount" v-model="amount" placeholder="-400">
                <small class="text-sm">(Negative: expenses | Positive: income)</small>
            </div>
            <div class="text-right">
                <button type="submit" class="btn btn-primary">Submit</button>
            </div>
        </form>
    </div>
</template>

<style scoped>
.title {
    font-size: 24px;
    font-weight: 500;
}

.form-group {
    margin: 15px 0;
}
.form-control {
    width: 100%;
    padding: 6px 10px;
    outline: none;
    border: none;
    border-radius: 5px;
    display: block;
    margin: 5px 0;
}

.text-right {
    text-align: right;
}

.text-sm {
    font-size: 10px;
}

.btn {
    border: none;
    padding: 10px 30px;
    border-radius: 10px;
    background-color: transparent;
}

.btn-primary {
    color: white;
    background-color: #1d4ed8;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
}
</style>