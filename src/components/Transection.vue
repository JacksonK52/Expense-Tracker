<script setup>

const submit = () => {

}
</script>

<template>
    <div>
        <h3 class="title">New Transaction</h3>
        <hr>
        <form @submit.prevent="submit">
            <div class="form-group">
                <label for="remark">Remark</label>
                <input type="text" class="form-control" name="remark" id="remark" placeholder="Chai and Biscuits" autofocus required>
            </div>
            <div class="form-group">
                <label for="amount">Amount</label>
                <input type="text" class="form-control" name="amount" id="amount" placeholder="-400" required>
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
    padding: 6px;
    outline: none;
    border: none;
    border-radius: 5px;
    display: block;
    margin: 5px 0;
}

.text-right {
    text-align: right;
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