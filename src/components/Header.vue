<template>
    <div>
        <div class="header">
            <div class="day">
                <p>Monday</p>
            </div>
            <div class="date">
                <p>13/10/2020</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Header'
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

    .day{
        margin-left: 50px;
        font-weight: bold;
    }

      .date{
        margin-right: 50px;
        letter-spacing: 3px;
    }
</style>