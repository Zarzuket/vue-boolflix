<template>
    <div>
        <div class="card">
            <img src="" alt="">
            <div>
                <h4 class="title"><span>Titolo :</span>{{serie.name}}</h4>
                <h4><span>Titolo originale:</span> {{serie.original_title}}</h4>
                <h4><span>Lingua:</span> {{serie.original_language}}</h4>
                <h4><span>Voto:</span> {{serie.vote_average}}</h4>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name:"Serie",
    props: ["serie"],
}   

</script>

<style lang="scss" scoped>
span{
    color: red;
    font-size: 20px;
}
.card{
    width: 12.5rem;
    height: 12.5rem;
    border: 1px solid green;
}
</style>