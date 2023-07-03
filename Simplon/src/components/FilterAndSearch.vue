<template>
    <div class="container pt-3 mb-1 justify-content-between bg-secondary border border-top-0 border-dark rounded-bottom-4">
        <div class="row">
            <div class="col-1"></div>
            <div class="form-check col-2 checkBox bg-light rounded">
                <input class="form-check-input" type="checkbox" value="Amis" v-model="checkedFilters.mesAmisChecked"
                    @change="handleFilterChange" />
                <label class="form-check-label" for="flexCheckDefault">
                    Mes amis
                </label>
            </div>
            <div class="form-check col-3 checkBox bg-light rounded">
                <input class="form-check-input" type="checkbox" value="Groupes" v-model="checkedFilters.mesGroupesChecked"
                    @change="handleFilterChange" />
                <label class="form-check-label" for="flexCheckDefault">
                    Mes groupes
                </label>
            </div>
            <div class="form-check col-3 checkBox bg-light rounded">
                <input class="form-check-input" type="checkbox" value="GroupesAdmin"
                    v-model="checkedFilters.mesGroupesAdminChecked" @change="handleFilterChange" />
                <label class="form-check-label" for="flexCheckDefault">
                    Mes groupes admin
                </label>
            </div>

            <div class="input-group mb-3 w-25 justify-content-end search">
                <button class="btn btn-outline-light" type="button" id="button-addon1">
                    <IconSearchVue />
                </button>
                <input type="text" class="form-control" placeholder="Recherche..."
                    aria-label="Example text with button addon" aria-describedby="button-addon1" v-model="searchQuery"
                    @input="handleSearch" />
            </div>
        </div>
    </div>
</template>
  
<script>
import IconSearchVue from "./icons/IconSearch.vue";
import { ref, getCurrentInstance, watch } from "vue";

export default {
    components: {
        IconSearchVue
    },
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
    setup(props, { emit }) {
        const checkedFilters = ref({
            mesAmisChecked: true,
            mesGroupesChecked: true,
            mesGroupesAdminChecked: true
        });

        const searchQuery = ref("");
        const filteredAmis = ref([]);
        const filteredGroupes = ref([]);
        const filteredGroupesAdmin = ref([]);

        const handleFilterChange = () => {
            emit("filterChange", checkedFilters.value);
        };

        const handleSearch = () => {
            const query = searchQuery.value.toLowerCase();
            filteredAmis.value = props.amis.filter(
                ami =>
                    (ami.pseudo && ami.pseudo.toLowerCase().includes(query)) ||
                    (ami.nom && ami.nom.toLowerCase().includes(query))
            );
            filteredGroupes.value = props.groupes.filter(
                groupe =>
                    (groupe.nom && groupe.nom.toLowerCase().includes(query))
            );
            filteredGroupesAdmin.value = props.groupes.filter(
                groupe =>
                    groupe.admin &&
                    (groupe.nom && groupe.nom.toLowerCase().includes(query))
            );
        };

        watch([props.amis, props.groupes], () => {
            handleSearch();
        });

        return {
            checkedFilters,
            searchQuery,
            filteredAmis,
            filteredGroupes,
            filteredGroupesAdmin,
            handleFilterChange,
            handleSearch
        };
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
  