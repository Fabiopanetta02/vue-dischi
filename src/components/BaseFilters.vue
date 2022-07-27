<template>
    <div class="col-10 col-lg-4 d-flex justify-content-end align-items-center">
        <label for="select">Filter by genre</label>
        <select name="genres" id="genres" class="rounded-pill" v-model="filter" @change="emitGenre">
            <option value="All">All</option>
            <option v-for="(genre, index) in genres" :key="index" :value="genre">
                {{genre}}
            </option>
        </select>
    </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name:'BaseFilters',
    data(){
        return{
            genres:[],
            filter:''
        }
    },
    mounted(){
        eventBus.$on('selectGenre', discs =>{
            discs.forEach(disc => {
                if(!this.genres.includes(disc.genre)){
                    this.genres.push(disc.genre);
                }
            });
        });
    },
    methods:{
        emitGenre(){
            eventBus.$emit('filters', this.filter);
        }
    }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/vars';
@import '@/assets/scss/style.scss';

label{
    display: inline-block;
    color:$light;
    font-size:.8rem;
    margin-right:20px;
    text-transform: uppercase;
}

select{
    background-color:$bg_main;
    border:none;
    color:$light;
    padding:5px 25px;
    border-right:25px solid transparent;

    &:focus-visible{
        outline:none;
    }
}

</style>