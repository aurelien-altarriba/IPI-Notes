<template>
    <footer>
        © {{ annee }} Aurélien ALTARRIBA - Site responsive
    </footer>
</template>

<script>
export default {
    name: "Footer",
    data: function() {
        return {
            annee: new Date().getFullYear()
        }
    }
}
</script>

<style scoped>
footer {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100vw;

    display: flex;
    justify-content: center;
    align-items: center;

    height: 1.3rem;
    font-size: 0.7rem;
    background-color: white;
    color: #666;
    border-top: 2px solid #ddd;
}
</style>