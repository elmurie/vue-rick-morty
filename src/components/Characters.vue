<template>
    <section class="characters container">
        <div class="row col-12">
            <SearchBar @search="searchCharacters" />
        </div>
        <div class="row">
            <div class="col-6 col-md-4 col-lg-3 mb-3" v-for="(element, index) in charactersFIltered" :key="index">
                <Character :info="element"/>
            </div>
        </div>
        
    </section>
</template>

<script>
import Character from './Character.vue';
import axios from 'axios';
import SearchBar from './SearchBar.vue';

export default {
    name : "Characters",
    components : {
        Character,
        SearchBar
    },
    data() {
        return {
            characters : [],
            searchText : ''
        }
    },
    created() {
        axios.get('https://api.sampleapis.com/rickandmorty/characters')
        .then( (response) => {
            this.characters = response.data;
        } );
    },
    methods: {
        searchCharacters(text) {
            this.searchText = text;
        }
    },
    computed: {
        charactersFIltered() {
            const arrFiltered =  this.characters.filter(
                (elm) => {
                    return elm.name.toLowerCase().includes(this.searchText.toLowerCase());
                }
            );
            return arrFiltered;
        }
    }
}
</script>

<style lang="scss" scoped>

</style>