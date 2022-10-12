<template>
    <div class="todo_container"> 
        <div class="input_container">
            <input 
                class="input_target" 
                :inputText="inputText" 
                @input="handleChange($event)"
            />
            <button @click="addItem"> Add </button>
        </div>

        <div class="todo_items_container">
            <TodoItem 
                v-for="(item, index) in todoItemText" 
                :key="item.id" 
                :text="item.text"
                @delete="deleteItem(index)"
            />
        </div>
    </div>
</template>

<script>
import TodoItem from "@/components/TodoList/TodoItem.vue";
import { defineComponent, ref } from "vue";

export default defineComponent ({
    components: {
        TodoItem
    },
    setup() {
        return {
            todoItemText: ref([
                {text: "This is one", id: 1},
                {text: "This is two", id: 2},
                {text: "This is three", id: 3},
                {text: "This is four", id: 4}
            ])
        }
    },
    data() {
        return {
            inputText: ''
        }
    },
    methods: {
        addItem() {
            let length = this.todoItemText.length;

            if (length < 8) {
                this.todoItemText[length] = {
                    text: this.inputText, id: length + 1
                }
                console.log(this.todoItemText)
            }
            
        },
        deleteItem(index) {
            console.log("call delete item")
            this.todoItemText.splice(index, 1)
        },
        handleChange(event) {
            this.inputText = event.target.value;
            console.log("handle change called")
        }
    }
    
});

</script>

<style scoped>

    .todo_container {
        background-color: rgb(255, 255, 255);
        width: 500px;
        margin: 4em auto;
        border-radius: 10px;
    }

    .input_container {
        padding: 2em 2em 4em 2em;
        margin: auto auto;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }

    .input_container input {
        width: 75%;
        border: 1px solid rgb(179, 179, 179);
        height: 40px;
        border-radius: 5px;
    }

    .input_container input:focus {
        outline: none !important;
        border: 1px solid rgb(53, 146, 252);
        -webkit-box-shadow: 0px 0px 5px 0px rgba(2,94,207,1);
        -moz-box-shadow: 0px 0px 5px 0px rgba(2,94,207,1);
        box-shadow: 0px 0px 5px 0px rgba(2,94,207,1);
    }

    .input_container button {
        width: 20%;
        border-radius: 5px;
        background-color: rgb(112, 160, 255);
    }
    
    .input_container button:hover {
        background-color: rgb(91, 134, 221);
        transition: background-color 0.1s;
    }

    .todo_items_container {
        display: grid;
        height: 500px;
        grid-template-columns: [first] 25% [line2] 25% [line3] 25% [line4] 25%;
        grid-template-rows: 
            [row1-start] 12.5% 
            [row1-end] 12.5% 
            [row2-start] 12.5% 
            [row2-end] 12.5%
            [row3-start] 12.5% 
            [row3-end] 12.5%
            [row4-start] 12.5% 
            [row4-end] 12.5%;
        background-color: rgb(255, 255, 255);
        border-radius: 10px;
        padding-bottom: 2em;
    }       

    @media only screen and (max-width: 550px) {
        .todo_container {
            width: 90%;
        }
    }

</style>
