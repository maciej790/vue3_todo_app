<template>
    <div>
        <Header />
        <Input />
        <TodoItem />
        <Clear />
    </div>
</template>

<script>

import Header from './Header.vue'
import Input from './Input.vue'
import TodoItem from './TodoItem.vue'
import Clear from './Clear.vue'

export default {
    name: 'Todo',
    components: {
        Header,
        Input,
        TodoItem,
        Clear
    }
}
</script>

<style scoped>

</style>