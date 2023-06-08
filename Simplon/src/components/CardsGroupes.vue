<template>
    <div class="" v-for="groupe in groupes" :key="groupe.id">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">{{ groupe.nom }}</h5>
            <p class="card-text">Description du groupe</p>
            <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
            <span class="supprimer delete-icon" @click="supprimerElement('groupe', groupe.id)">&times;</span>
          </div>
          <ul class="list-group list-group-flush">
            <li class="list-group-item" v-for="membre in groupe.membres" :key="membre.id">
              {{ membre.nom }}
            </li>
          </ul>
        </div>
      </div>
</template>

<script>
import IconPersonDelete from './icons/IconPersonDelete.vue';
import IconProfile from './icons/IconProfile.vue';

export default {
  props: {
    amis: {
      type: Array,
      default: () => []
    },
    groupes: {
      type: Array,
      default: () => []
    }
  },
  components: { IconProfile, IconPersonDelete },
  methods: {
    supprimerElement(id) {
        this.$emit('supprimer-groupe', id);
      }
    
  }
};
</script>