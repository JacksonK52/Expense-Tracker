<script setup>

</script>

<template>
    <div >
        <h3 class="title">History</h3>
        <hr>
        <ul class="unorder-list">
            <li class="list plus">
                <p>Salary</p>
                <p><span class="font-hindi">₹</span> 10000</p>
            </li>
            <li class="list minus">
                <p>Food</p>
                <p><span class="font-hindi">₹</span> -100</p>
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
    margin-top: 10px;
    padding: 5px 10px;
    background-color: var(--white);
    list-style-type: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.minus {
    border-left: 5px solid var(--danger);
}

.plus {
    border-left: 5px solid var(--success);
}
</style>