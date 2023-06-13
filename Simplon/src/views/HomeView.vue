<script setup>
import AddFriends from "../components/ButtonFriends.vue";
import FilterAndSearch from '../components/FilterAndSearch.vue';
import Cards from '../components/Cards.vue';
import CardsGroupes from '../components/CardsGroupes.vue';
</script>

<template>
  <main>
    <AddFriends />
            <FilterAndSearch />
            <div class="container pt-3 bg-secondary border border-top-0 border-dark rounded rounded-4">

                <div v-if="(amis.length != 0 || groupes.length != 0)" class="row">
                    <div class="col-md-4 mb-3" v-for="ami in amis" :key="ami.id">
                        <Cards :amis="[ami]" @supprimer-ami="supprimerAmi(ami.id)" />
                    </div>
                    <div class="col-md-4 mb-3" v-for="groupe in groupes" :key="groupe.id">
                        <CardsGroupes :groupes="[groupe]" @supprimer-groupe="supprimerGroupe(groupe.id)" />
                    </div>
                </div>
                <div v-else>
                    <div class="alert alert-warning d-flex align-items-center" role="alert">
                        <svg xmlns="http://www.w3.org/2000/svg" class="bi bi-exclamation-triangle-fill flex-shrink-0 me-2"
                            width="16" height="16" viewBox="0 0 16 16" role="img" aria-label="Warning:">
                            <path
                                d="M8.982 1.566a1.13 1.13 0 0 0-1.96 0L.165 13.233c-.457.778.091 1.767.98 1.767h13.713c.889 0 1.438-.99.98-1.767L8.982 1.566zM8 5c.535 0 .954.462.9.995l-.35 3.507a.552.552 0 0 1-1.1 0L7.1 5.995A.905.905 0 0 1 8 5zm.002 6a1 1 0 1 1 0 2 1 1 0 0 1 0-2z" />
                        </svg>
                        <div>
                            An example alert with an icon
                        </div>
                    </div>
                </div>
            </div>
  </main>
</template>

<script>

export default {
    data() {
        return {
            amis: [
                {
                    id: 1,
                    pseudo: "alice91",
                    nom: "Alice",
                    photo: "https://example.com/photos/alice.jpg"
                },
                {
                    id: 2,
                    pseudo: "bob23",
                    nom: "Bob",
                    photo: "https://example.com/photos/bob.jpg"
                },
                {
                    id: 3,
                    pseudo: "charlie",
                    nom: "Charlie",
                    photo: "https://example.com/photos/charlie.jpg"
                }
            ],
            groupes: [
                {
                    id: 4,
                    nom: "Groupe 1",
                    membres: [
                        { pseudo: "alice91", nom: "Alice", photo: "https://example.com/photos/alice.jpg" },
                        { pseudo: "bob23", nom: "Bob", photo: "https://example.com/photos/bob.jpg" }
                    ]
                },
                {
                    id: 5,
                    nom: "Groupe 2",
                    membres: [
                        { pseudo: "bob23", nom: "Bob", photo: "https://example.com/photos/bob.jpg" },
                        { pseudo: "charlie", nom: "Charlie", photo: "https://example.com/photos/charlie.jpg" }
                    ]
                }
            ]
        };
    },
    methods: {
        supprimerAmi(id) {
            this.amis = this.amis.filter(ami => ami.id !== id);
            console.log(this.amis)
            console.log(this.amis.length != 0 || this.groupes.length != 0)
        },
        supprimerGroupe(id) {
            this.groupes = this.groupes.filter(groupe => groupe.id !== id);
            console.log(this.groupes)
            console.log(this.amis.length != 0 || this.groupes.length != 0)
        }
    },
};
</script>
