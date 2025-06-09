<template>
    <div id="container">
        <div id="first-row">
            <button @click="$emit('attack')">Attack</button>
            <button :disabled="flag1" @click="specialAttack">Special Attack</button>
        </div>
        <div id="second-row">
            <button :disabled="flag2" @click="heal">Heal</button>
            <button>Surrender</button>
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            flag1: false,
            flag2: false
        }
    },
    methods:{
        specialAttack(){
            this.$emit('special-attack');
            this.flag1 = true;
        },
        heal(){
            this.$emit('heal');
            this.flag2 = true;
        }
    }
}
</script>

<style scoped>
#container{
    margin: 60px
}
#first-row{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 80px;
    margin-bottom: 40px;
}
#second-row{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 80px;
}
button{
    color: white;
    border-radius: 7px;
    background-color: purple;
    width: 200px;
    height: 100px;
    font-size: 20px;
    font-family: roboto;
}
</style>