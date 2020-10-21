<template>
    <div>
        <div class="header">
            <div class="title">
                <p>Todo list</p>
            </div>
            <div class="date">
                <p>{{date}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Header',

    props:{
        date: Number
    }
}
</script>

<style scoped>
    .header{
        width: 100%;
        height: 65px;
        border-radius: 20px;
        background-color: white;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }


    p{
        font-size: 25px;
        color: #487B8B;
    }

    .title{
        margin-left: 50px;
        font-weight: bold;
    }

      .date{
        margin-right: 50px;
        letter-spacing: 3px;
    }

    @media (max-width: 900px) {
     p {
        font-size: 18px;
    }
    .header{
            height: 50px;
    }

    .title{
        margin-left: 20px;
    }

    .date{
        margin-right: 20px;
    }
      
}
</style>