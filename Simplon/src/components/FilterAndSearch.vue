<script setup>
import IconSearchVue from "./icons/IconSearch.vue";

</script>
<template>
    <div class="container pt-3 mb-1 justify-content-between bg-secondary border border-top-0  border-dark rounded-bottom-4">
        <div class="row">
            <div class="col-1"></div>
            <div class="form-check col-2 checkBox bg-light rounded">
                <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault">
                <label class="form-check-label" for="flexCheckDefault">
                    Mes amis
                </label>
            </div>
            <div class="form-check col-3 checkBox bg-light rounded">
                <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault">
                <label class="form-check-label" for="flexCheckDefault">
                    Mes groupes
                </label>
            </div>
            <div class="form-check col-3 checkBox bg-light rounded">
                <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault">
                <label class="form-check-label" for="flexCheckDefault">
                    mes groupes admin
                </label>
            </div>


            <div class="input-group mb-3 w-25 justify-content-end search">
                <button class="btn btn-outline-light" type="button" id="button-addon1">
                    <IconSearchVue />
                </button>
                <input type="text" class="form-control" placeholder="Research..." aria-label="Example text with button addon"
                    aria-describedby="button-addon1">
            </div>
        </div>
    </div>
</template>

<style>
.checkBox{    
width: auto;
    height: fit-content;
    padding: 5px;
    margin-right: 13%;
}
.search{
    margin-left: auto;
}

</style>