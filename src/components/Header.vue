<template>
  <nav>
      <div class="logo">
          LOGO
      </div>
      <input type="text" v-model="search">
      <button @click="$emit('sendsearch' , search)" @>Esegui Ricerca</button>
  </nav>
</template>

<script>
export default {
name: "Header",
data(){
    return{
        search: "",
    }
}
}
</script>

<style lang="scss" scoped>
nav{
    display: flex;
    justify-content: space-between;
    input{
        margin-left: auto;
    }
    
}

</style>