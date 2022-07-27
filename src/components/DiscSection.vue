<template>
  <main>
    <div class="container">
      <div class="discs-list row">
        <div class="col" v-for="(disc, i) in filteredDiscs" :key="i">
          <DiscCard 
          :datas="disc"/>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios';
import DiscCard from './DiscCard.vue';
import {eventBus} from '../main.js';

export default {
    name: "DiscSection",
    components: { 
      DiscCard 
    },
    data() {
        return { 
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            discs: [],
            test: [],
            loading: true,
            selectedGenre: 'All'
        };
    },
    created(){
          this.getDiscs(); 
          eventBus.$on('filters', el =>{
              this.selectedGenre = el;
          });     
    },
    computed:{
    filteredDiscs(){
        if(this.selectedGenre == 'All'){
          return this.discs;
        }
        return this.discs.filter(disc => disc.genre == this.selectedGenre);
    }
  },
  methods:{
      getDiscs(){
        axios
        .get(this.apiUrl)
        .then (response =>{
          this.discs = response.data.response;
          this.loading = false;
          this.selectedGenre = 'All';
          eventBus.$emit('selectGenre', this.discs);
        })
        .catch(err => console.log(err));
      }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/vars";
  main{
    background-color: $bg_main;
    height: 90vh;

    .discs-list{
      padding-top: 100px
    }
  }
</style>