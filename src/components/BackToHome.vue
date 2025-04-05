<template>
    <div class="btn-home">
        <button>
            <img src="../assets/back.png">
        </button>
    </div>
</template>

<script>
    export default {
        name: 'BackToHome',
    }
</script>

<style scoped>
    .btn-home {
        position: absolute;
        left: 20px;
        top: 20px;
    }
    .btn-home button {
        height: 50px;
        width: 50px;
        border-radius: 50%;
        border: none;
        background-color: darkslateblue;
        color: white;
        align-items: center;
        justify-content: center;
        transition: width 0.2s ease, border-radius 0.2s ease, border-color 0.2s ease, color 0.2s ease;
    }
    .btn-home button:hover{
        width: 120px;
        border-radius: 5px;
        border: 1px solid darkslateblue;
        background-color: v-bind(bgColor);
        color: darkslateblue;
    }
</style>