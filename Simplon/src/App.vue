<script setup>
import HelloWorld from './components/HelloWorld.vue';
import Navbar from './components/Navbar.vue';
import AddFriends from "./components/AddFriends.vue";
import FilterAndSearch from './components/FilterAndSearch.vue';
import Cards from './components/Cards.vue';
import CardsGroupes from './components/CardsGroupes.vue';



</script>

<template>
  <div>
    <header>
      <Navbar />
    </header>
    <main>
      <AddFriends />
      <FilterAndSearch />
      <div class="container pt-3 justify-content-between bg-secondary border border-top-0 border-dark rounded rounded-4">
    <div class="row"  >
      <div class="col-md-4 mb-3" v-for="ami in amis" :key="ami.id" >
        <Cards :amis="[ami]" @supprimer-ami="supprimerAmi(ami.id)" />
      </div>
      <div class="col-md-4 mb-3" v-for="groupe in groupes" :key="groupe.id" >
        <CardsGroupes :groupes="[groupe]" @supprimer-groupe="supprimerGroupe(groupe.id)" />

      </div>
  </div></div>
    </main>

  </div>
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
        },
        supprimerGroupe(id) {
            this.groupes = this.groupes.filter(groupe => groupe.id !== id);
        }
    },
    components: { CardsGroupes }
};
</script>

<style scoped></style>
