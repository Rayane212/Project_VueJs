<script setup>
import AddFriends from "../components/ButtonFriends.vue";
import FilterAndSearch from '../components/FilterAndSearch.vue';
import Cards from '../components/Cards.vue';
import CardsGroupes from '../components/CardsGroupes.vue';
import { ref } from 'vue';

</script>
<template>
    <main>
        <AddFriends />
        <FilterAndSearch v-model:checkedFilters="checkedFilters" @filterChange="updateContent" :amis="amis"
            :groupes="groupes" />
        <div class="container pt-3 bg-secondary border border-top-0 border-dark rounded rounded-4">
            <div v-if="hasFilteredResults" class="row">
                <div class="col-md-4 mb-3" v-for="ami in filteredAmis" :key="ami.id">
                    <Cards :amis="[ami]" @supprimer-ami.passive="supprimerAmi(ami.id)" />
                </div>
                <div class="col-md-4 mb-3" v-for="groupe in filteredGroupes" :key="groupe.id">
                    <CardsGroupes :groupes="[groupe]" @supprimer-groupe.passive="supprimerGroupe(groupe.id)" />
                </div>
                <div class="col-md-4 mb-3" v-for="groupe in filteredGroupesAdmin" :key="groupe.id">
                    <CardsGroupes :groupes="[groupe]" @supprimer-groupe.passive="supprimerGroupe(groupe.id)" />
                </div>
            </div>
            <div v-else>
                <div class="d-flex justify-content-center">
                    <img src="../assets/friends.png" alt="friends">
                </div>
            </div>
        </div>
    </main>
</template>
  
<script>
export default {
    components: {
        AddFriends,
        FilterAndSearch,
        Cards,
        CardsGroupes
    },
    data() {
        return {
            amis: [
                {
                    id: 1,
                    pseudo: "alice91",
                    nom: "Alice",
                    description: "",
                    photo: "https://example.com/photos/alice.jpg",
                    codeGroupe: "groupe1"
                },
                {
                    id: 2,
                    pseudo: "bob23",
                    nom: "Bob",
                    description: "",
                    photo: "https://example.com/photos/bob.jpg",
                    codeGroupe: "groupe1"
                },
                {
                    id: 3,
                    pseudo: "charlie",
                    nom: "Charlie",
                    description: "",
                    photo: "https://example.com/photos/charlie.jpg",
                    codeGroupe: "groupe2"
                }
            ],
            groupes: [
                {
                    id: 4,
                    nom: "Groupe 1",
                    description: "",
                    admin: true,
                    codeGroupe: "groupe1"
                },
                {
                    id: 5,
                    nom: "Groupe 2",
                    description: "",
                    admin: false,
                    codeGroupe: "groupe2"
                }
            ],
            checkedFilters: {
                mesAmisChecked: true,
                mesGroupesChecked: true,
                mesGroupesAdminChecked: true
            }
        };
    },
    computed: {
        filteredAmis() {
            return this.checkedFilters.mesAmisChecked ? this.amis : [];
        },
        filteredGroupes() {
            return this.checkedFilters.mesGroupesChecked ? this.groupes.filter(groupe => !groupe.admin) : [];
        },
        filteredGroupesAdmin() {
            return this.checkedFilters.mesGroupesAdminChecked ? this.groupes.filter(groupe => groupe.admin) : [];
        },
        hasFilteredResults() {
            return (
                this.filteredAmis.length > 0 ||
                this.filteredGroupes.length > 0 ||
                this.filteredGroupesAdmin.length > 0
            );
        }
    },
    methods: {
        supprimerAmi(id) {
            this.amis = this.amis.filter(ami => ami.id !== id);
        },
        supprimerGroupe(id) {
            this.groupes = this.groupes.filter(groupe => groupe.id !== id);
        },
        updateContent(checkedFilters) {
            this.checkedFilters = checkedFilters;
        }
    }
};
</script>
  