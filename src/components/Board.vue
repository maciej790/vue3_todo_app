<template>
    <div class="board">
        <Header />
        <Input 
            @handle-from-child = 'handleFromChild($event)' 
            @handle-add-item="addItem"
        />
        <TodoItem />

        <p v-for="item in state.tasks" :key="item.id">
            {{item.title}}
        </p>
    </div>
</template>

<script>

import Header from './Header.vue'
import Input from './Input.vue'
import TodoItem from './TodoItem.vue'

import { reactive } from 'vue'
export default {
    name: 'Board',
    components: {
        Header,
        Input,
        TodoItem,
    },

    setup(){

        const state = reactive({
            inputValue: '',
            tasks: [
                {id: Math.random() ,title: 'go for a walk', complete: false},
                {id: Math.random() ,title: 'learn a vue', complete: false},
                {id: Math.random() ,title: 'learn a react', complete: false}
            ]
        })

     
        const handleFromChild = (payload) =>{
            state.inputValue = payload
        }

        const addItem = () =>{
            state.tasks.push({
                id: Math.random(),
                title: state.inputValue,
                complete: false
            })

        }

    return{
        state,
        handleFromChild,
        addItem
    }
    }
}
</script>

<style>
    .board{
        width: 50%;
        height: 500px;
        background-color: rgba(255, 255, 255, 0.8);
        margin-left: auto;
        margin-right: auto;
        margin-top: 100px;
        border-radius: 20px;
        display: flex;
        flex-direction: column;
    }

</style>