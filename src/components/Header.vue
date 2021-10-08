<template>
  <nav>
      <div class="logo">
          <h1>BOOLFLIX</h1>
      </div>
      <input type="text" v-model="search" placeholder="Inserisci il film da cercare">
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
    height: 100px;
    padding: 1.25rem 1.25rem;
    h1{
        color: red;
        box-shadow: 5px 10px 18px red;
    }
    input{
        margin-left: auto;
        height: 2.25rem;
        outline: none;
        background-color: grey;
        color: red;
        background-color: black;
    }
    button{
        height: 2.25rem;
        color: red;
        background-color: black;
        box-shadow: 5px 10px 18px red;;
    }
}

</style>