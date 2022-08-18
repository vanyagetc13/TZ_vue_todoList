<template>
    <input class="input" type="text" :placeholder=placeholder />
</template>

<script>
export default {
    props: {
        placeholder: {
            type: String,
            required: false
        }
    }
}
</script>

<style>
.input {
    border: 1px solid rgba(40, 40, 70, 0.1);
    border-radius: 8px;
    padding: 8px 15px;
}
</style>