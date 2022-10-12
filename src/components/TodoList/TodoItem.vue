<template>
    <div class="todo_item" key="index"> 
            <p class="text"> {{text}} </p>
            <button class="button" @click="callDeleteItem('index')"> 
               DELETE
            </button>
    </div>
</template>

<script>

export default {
    props: ["text", "id", "deleteItem"],
    methods: {
        callDeleteItem(id) {
            this.$emit('delete', id)
        }
    }
}
</script>

<style scoped>
    .todo_item {
        background-color:rgb(172, 204, 225);
        grid-column: first / span 4;
        border: solid 1px rgb(166, 166, 166);
        height: 80%;
        margin: 0 2em;
        display: grid;
        grid-template-columns: [first] 25% [line2] 25% [line3] 25% [line4] 25%;
        border-radius: 5px;
        transition: box-shadow 0.1s;
    }
    
    .todo_item:hover {
        -webkit-box-shadow: 0px 0px 5px 0px rgba(2,94,207,1);
        -moz-box-shadow: 0px 0px 5px 0px rgba(2,94,207,1);
        box-shadow: 0px 0px 5px 0px rgba(2,94,207,1);
    }

    .text {
        grid-column-start: first;
        grid-column-end: span 3;
        padding-left: 10px;
    }

    .button {
        height: 80%;
        margin-right: 1em;
        border-radius: 10px;
        border: none !important;
        background-color: rgb(17, 67, 202);
        color: white;
        align-self: center;
        grid-column-start: line4;
        grid-column-end: span 1;
    }
    
    .button:hover {
        background-color: rgb(70, 109, 217);
        transition: background-color 0.1s;
    }

</style>
