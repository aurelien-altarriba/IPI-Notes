<template>
    <div>
        <input
                type="text"
                class="val_note"
                :value="note.content"
                v-on:change.passive="modifier($event, note)"
        >
        <div class="group-btn">
            <span class="badge badge-info compteur">{{ compteur(note) }}</span>
            <button type="button" class="btn btn-danger" v-on:click="supprimer(note)">X</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Note"
    }
</script>

<style scoped>

</style>