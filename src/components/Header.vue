<template>
    <header>
        IPI'Notes
    </header>
</template>

<script>
    export default {
        name: "Header"
    }
</script>

<style scoped>
header {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 2.5rem;
    margin-bottom: 3rem;
    text-shadow: 0 0 1px #eee;

    border-radius: 0 0 70% 70%;
    background: linear-gradient(4deg, white 28%, #fee 83%);
    box-shadow: 0 0 5px #ccc;

    width: 100%;
    height: 6rem;
}
</style>