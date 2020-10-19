<template>
    <div>
        <div class="item_box">
            <div class="item">
                <div class="item__title">
                    
                </div>
                <div class="item__btn">
                    <i class="fas fa-trash fa-2x"></i>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TodoItem'
    //<i class="fas fa-check"></i>
}
</script>

<style scoped>
    .item_box{
        width: 100%;
        height: auto;
        margin-top: 30px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .item{
        width: 80%;
        height: 50px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-top: 30px;
    }

    .item__title{
        width: 80%;
        height: 50px;
        border-radius: 20px;
        background-color: #46C287;
    }

    .item__btn{
        width: 50px;
        height: 50px;
        border-radius: 20px;
        background-color: #46C287;
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
    }
</style>