<template>
    <div class="container">
        <div class="top-container">
            <h1 :style="{color: numColor}">
                {{ num }}
            </h1>
        </div>
        <div class="bottom-container">
            <button @click="decrementNumber">Decrement</button>
            <button @click="incrementNumber">Increment</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'NumCounter',
        data() {
            return {
                num: 0,
                numColor: 'darkslateblue'
            }
        },
        methods: {
            decrementNumber() {
                this.num--
                this.changeColor()
            },
            incrementNumber() {
                this.num++
                this.changeColor()
            },
            changeColor() {
                if(this.num > 0) {
                    this.numColor = 'green'
                } else if(this.num < 0) {
                    this.numColor = 'red'
                } else {
                    this.numColor = 'darkslateblue'
                }
            }
        }
    }
</script>

<style scoped>
    .container button {
        margin-inline: 5px;
        width: 25%;
    }
</style>