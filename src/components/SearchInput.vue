<template>
    <input 
        type="text" 
        placeholder="Type Your location here" 
        :value="value" 
        @change='emitEvent'
        :class="{ top }"
    />
</template>

<script>
export default {
    name: 'SearchInput',

    props: {
        value:{
            type: String,
            required: true
        },

        top:{
            type: Boolean,
            defoult: false
        }
        
    },
    
    setup(props, {emit}){
        
        const emitEvent = (e) =>{
            emit('emit-from-input', e.target.value)
        }

        return{
            emitEvent
        }
    }
}
</script>

<style lang="scss" scoped>
    input{
        width: 30%;
        height: 40px;
        text-align: center;
        color: white;
        background-color: transparent;
        outline: none;
        border: none;
        border-bottom: 2px solid white;
    }

    ::placeholder{
        color: white;
        font-size: 15px;
    }

    .top{
        position: absolute;
        top: 20px;
    }

</style>