<script setup>

const props = defineProps({
    title: {
        type: String,
        required: true
    },
    by: {
        type: String,
        required: true
    }
})
</script>

<template>
    <div class="header mb-2">
        <h1>{{ props.title }}</h1>
        <small class="header-by">by {{ props.by }}</small>
    </div>
</template>

<style scoped>
.header {
    background-color: var(--gray);
    padding: 10px 20px;
    border-radius: 10px;
    color: var(--white);
    
}

.header-by {
    font-weight: 300;
    color: var(--light-gray);
}
</style>