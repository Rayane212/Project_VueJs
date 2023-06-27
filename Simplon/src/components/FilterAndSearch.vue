<template>
    <div class="container pt-3 mb-1 justify-content-between bg-secondary border border-top-0 border-dark rounded-bottom-4">
      <div class="row">
        <div class="col-1"></div>
        <div class="form-check col-2 checkBox bg-light rounded">
          <input class="form-check-input" type="checkbox" value="Amis" v-model="checkedFilters.mesAmisChecked"
            @change="handleFilterChange">
          <label class="form-check-label" for="flexCheckDefault">
            Mes amis
          </label>
        </div>
        <div class="form-check col-3 checkBox bg-light rounded">
          <input class="form-check-input" type="checkbox" value="Groupes" v-model="checkedFilters.mesGroupesChecked"
            @change="handleFilterChange">
          <label class="form-check-label" for="flexCheckDefault">
            Mes groupes
          </label>
        </div>
        <div class="form-check col-3 checkBox bg-light rounded">
          <input class="form-check-input" type="checkbox" value="GroupesAdmin"
            v-model="checkedFilters.mesGroupesAdminChecked" @change="handleFilterChange">
          <label class="form-check-label" for="flexCheckDefault">
            Mes groupes admin
          </label>
        </div>
  
        <div class="input-group mb-3 w-25 justify-content-end search">
          <button class="btn btn-outline-light" type="button" id="button-addon1">
            <IconSearchVue />
          </button>
          <input type="text" class="form-control" placeholder="Research..."
            aria-label="Example text with button addon" aria-describedby="button-addon1">
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import IconSearchVue from "./icons/IconSearch.vue";
  import { getCurrentInstance, ref } from 'vue';
  
  export default {
    setup() {
      const checkedFilters = ref({
        mesAmisChecked: true,
        mesGroupesChecked: true,
        mesGroupesAdminChecked: true
      });
  
      const instance = getCurrentInstance();
  
      function handleFilterChange() {
        instance.emit('filterChange', checkedFilters.value);
      }
  
      return {
        checkedFilters,
        handleFilterChange
      };
    },
    components: {
      IconSearchVue
    }
  };
  </script>
  
  <style>
  .checkBox {
    width: auto;
    height: fit-content;
    padding: 5px;
    margin-right: 13%;
  }
  
  .search {
    margin-left: auto;
  }
  </style>
  