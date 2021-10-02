<template>
    <section class="characters container">
        <div class="row">
            <div class="col-6 col-md-4 col-lg-3 mb-3" v-for="(element, index) in characters" :key="index">
                <Character :info="element"/>
            </div>
        </div>
        
    </section>
</template>

<script>
import Character from './Character.vue';
import axios from 'axios';
export default {
    name : "Characters",
    components : {
        Character
    },
    data() {
        return {
            characters : []
        }
    },
    created() {
        axios.get('https://api.sampleapis.com/rickandmorty/characters')
        .then( (response) => {
            this.characters = response.data;
        } );
    }
}
</script>

<style lang="scss" scoped>

</style>