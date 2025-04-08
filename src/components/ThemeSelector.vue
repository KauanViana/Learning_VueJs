<template>
    <div class="btn-theme">
        <button @click="onClick" @mouseover="onMouseOver" @mouseout="onMouseOut">
            <img v-if="!isMouseOver" src="../assets/theme.png">
            {{ txt }}
        </button>
    </div>
</template>

<script>
    export default {
        name: 'ThemeSelector',
        data() {
            return {
                bgColor: 'White',
                isMouseOver: false,
                txt: '',
                textColor: 'White'
            }
        },
        methods: {
            onClick() { this.changeTheme()},
            changeTheme() {
                switch (this.bgColor){
                    case 'White':
                        this.bgColor = '#323232'
                        this.txt = 'Dark Theme'
                        this.textColor = 'White'
                        break
                        case '#323232':
                            this.bgColor = 'White'
                            this.txt = 'Light Theme'
                            this.textColor = '#2c3e50'
                        break                        
                }
                document.body.style.backgroundColor = this.bgColor
            },
            onMouseOver() { 
                this.isMouseOver = true 
                if (this.bgColor === '#323232') { this.txt = 'Dark Theme' }
                else {   this.txt = 'Light Theme'   }
            },    
            onMouseOut() { 
                this.isMouseOver = false 
                this.txt = ''
            }
        }
    }
</script>

<style scoped>
    .btn-theme {
        position: fixed;
        right: 20px;
        bottom: 20px;
    }
    .btn-theme button {
        height: 50px;
        width: 50px;
        border-radius: 50%;
        align-items: center;
        justify-content: center;
        transition: width 0.2s ease, border-radius 0.2s ease, border-color 0.2s ease, color 0.2s ease;
    }
    .btn-theme button:hover{
        width: 100px;
        border-radius: 5px;
    }
</style>