<template>
  <div class="disc-card text-center p-4 mb-5">
    <img :src="datas.poster" :alt="datas.title" class="mb-3">
    <h4 class="mb-3">{{datas.title.toUpperCase()}}</h4>
    <div class="author">{{datas.author}}</div>
    <div class="year">{{datas.year}}</div>
  </div>
</template>

<script>
export default {
    name: 'DiscCard',
    props: ["datas"]
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/vars";
.disc-card{
    background-color: $bg_disc;
    height: 400px;

    img{
        width: 190px;
        height: 190px
    };

    h4{
        color: #fff;
    }

    .author{
        color: $color_description;
        font-size: 18px;
        font-weight: bold;
    }

    .year{
        color: $color_description;
    }
}
</style>