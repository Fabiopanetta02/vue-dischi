<template>
  <main>
    <div class="container">
      <div class="discs-list row">
        <div class="col" v-for="disc in discs" :key="disc.title">
          <DiscCard :title="disc.title" :image="disc.poster" :author="disc.author" :year="disc.year"/>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios';
import DiscCard from './DiscCard.vue';
export default {
    name: "DiscSection",
    components: { DiscCard },
    data() {
        return {
            discs: []
        };
    },
    mounted() {
        axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((res) => {
            this.discs = res.data.response;
        });
    },
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