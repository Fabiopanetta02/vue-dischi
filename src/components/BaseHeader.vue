<template>
  <header class="d-flex justify-content-between container-fluid">
    <div class="p-2">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/2048px-Spotify_logo_without_text.svg.png" alt="" class="h-100">
    </div>

    <BaseFilters />
  </header>
</template>

<script>
import BaseFilters from './BaseFilters.vue';
export default {
    name: 'BaseHeader',
    components: {
        BaseFilters
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/vars";
    header{
        background-color: $bg_header;
        height: 10vh;

        div{
            height: 10vh;
        }
    }
</style>