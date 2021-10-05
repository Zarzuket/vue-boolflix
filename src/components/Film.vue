<template>
  <div class="container">
      <div class="card">
          <img src="" alt="">
          <h4 class="title">{{info.title}}</h4>
          <h4>{{info.original_title}}</h4>
          <h4>{{info.original_language}}</h4>
          <h4>{{info.vote_average}}</h4>
      </div>
  </div>
</template>

<script>


export default {
    name:"Film",
    props: ["info"],
}   

</script>

<style lang="scss" scoped>
.container{
    display: flex;
}
.card{
    width: 12.5rem;
    height: 12.5rem;
    border: 1px solid red;
}
</style>