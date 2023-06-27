<template>
  <div class="" v-for="groupe in groupes" :key="groupe.id">
    <div class="card">
      <IconGroup />
      <div class="card-body">
        <h5 class="card-title">{{ groupe.nom }}</h5>
        <p class="card-text">{{ groupe.description }}</p>
        <span class="supprimer delete-icon" @click="supprimerElement('groupe', groupe.id)">&times;</span>
      </div>
    </div>
  </div>
</template>

<script>
import IconGroup from './icons/IconGroup.vue';

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
  emits: ['supprimer-groupe-passive'],
  components: { IconGroup },
  methods: {
    supprimerElement(id) {
      this.$emit('supprimer-groupe-passive', id);
    }

  }
};
</script>