<template>
    <header>
        <img src="https://fontmeme.com/permalink/211006/c072857f28ffed69c9266a55183f4c20.png" alt="Boolflix Logo">
        <form>
            <input v-model="userInput" type="text" placeholder="Cerca un film o una serie">
            <button @click.prevent="$emit('search', userInput)">CERCA</button>
        </form>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            userInput: ''
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common.scss';
    header {
        display: flex;
        background-color: #222;
        align-items: center;
        justify-content: space-between;
        padding: 15px;
        input {
            width: 200px;
            height: 35px;
            border-radius: 5px;
            padding: 10px;
        }
        button {
            padding: 5px 25px;
            border-radius: 5px;
            margin: 0 20px;
            background-color: $redColor;
            color: #222;
            font-weight: bold;
            border: none;
        }
    }
</style>