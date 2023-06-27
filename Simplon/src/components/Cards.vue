<template>
  <div class="" v-for="ami in amis" :key="ami.id">
    <div class="card">
      <IconProfile />
      <!-- <img :src="ami.photo" class="card-img-top" :alt="ami.nom"> -->
      <div class="card-body">
        <h5 class="card-title">{{ ami.nom }}</h5>
        <p class="card-text">{{ ami.description }}</p>
        <span class="supprimer delete-icon" @click="supprimerElement('ami', ami.id)">
          <a>
            <IconPersonDelete />
          </a>
        </span>
      </div>
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
  emits: ['supprimer-ami-passive'],
  components: { IconProfile, IconPersonDelete },
  methods: {
    supprimerElement(id) {

      this.$emit('supprimer-ami-passive', id);

    }
  }
};
</script>

<style>
.delete-icon {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  cursor: pointer;
}
</style>
