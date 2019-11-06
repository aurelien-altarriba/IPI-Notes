<template>
    <div class="body">
        <div class="liste">
            <p v-if="liste.length < 1">Aucune note inscrite :(</p>
            <ul class="list-group list-group-flush" id="liste_notes">
                <li class="list-group-item note" v-for="note in liste" :key="note.id">
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
                </li>
            </ul>

            <div id="bloc_add">
                <span class="badge badge-pill badge-secondary compteurAdd">{{ compteurAdd(note) }}</span>
                <textarea
                    class="form-control"
                    id="txt_note"
                    rows="2"
                    v-model.trim="note"
                    placeholder="Écrivez ce à quoi vous pensez!"
                ></textarea>
            </div>
            <button type="button" class="btn btn-primary" id="ajouter" v-on:click="ajouter()">
                Ajouter la note
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            liste: [],
            note: ""
        }
    },
    methods: {
        ajouter() {
            let newNote = {
                id: Date.now(),
                content: this.note,
            };

            if (this.note.length > 0) {
                this.liste.push(newNote);
                localStorage.setItem('listeNotes', JSON.stringify(this.liste));
            }
        },
        supprimer(note) {
            this.liste = this.liste.filter((liste) => liste.id !== note.id);
            localStorage.setItem('listeNotes', JSON.stringify(this.liste));
        },
        modifier(event, note) {
            let indexOld = this.liste.indexOf(note);
            this.liste[indexOld].content = event.target.value;
            localStorage.setItem('listeNotes', JSON.stringify(this.liste));
        },
        compteur(note) {
            let nb = note.content.length;
            return nb > 1 ? nb + " caractères" : nb + " caractère"
        },
        compteurAdd(note) {
            let nb = note.length;
            return nb > 1 ? nb + " caractères" : nb + " caractère"
        }
    },
    mounted: function () {
        this.liste = JSON.parse(localStorage.getItem('listeNotes')) || []
    }
}
</script>

<style scoped>
.liste {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    padding: 1rem;
    min-width: 40vw;
    box-shadow: 0 0 4px #ccc;
    border-radius: 1rem;
    background-color: white;
}

.note {
    padding: 0.5rem;
    min-width: 40vw;

    display: flex;
    justify-content: space-between;
    align-items: center;
}

.group-btn {
    display: flex;
    align-items: center;
}
.val_note {
    border: 2px solid white;
    border-radius: 0.2rem;
    padding: 0.5rem;
    transition: all 0.2s ease-in-out;
    width: 70%;
}

.val_note:hover {
    border: 2px solid grey;
    background-color: #fafafa;
}

.compteur {
    white-space: nowrap;
    margin-right: 0.5rem;
    font-size: 0.7rem;
    box-shadow: 0 0 1px grey;
}

.compteurAdd {
    white-space: nowrap;
    margin: 3rem 0 0.5rem;
}

.note .btn {
    border-radius: 100%;
    box-shadow: 0 0 2px grey;
    width: 1.5rem;
    height: 1.5rem;
    font-size: 0.8rem;
    margin: 0.2rem;

    display: flex;
    justify-content: center;
    align-items: center;
}

#bloc_add {
    display: flex;
    flex-direction: column;
    align-items: center;
}

#txt_note {
    min-width: 30vw;
}

#ajouter {
    font-size: 1.2rem;
    margin: 1rem;
}

/* CHANGEMENT EN MOBILE */
@media all and (max-width: 1000px) {
    .note {
         flex-direction: column;
     }
}
</style>