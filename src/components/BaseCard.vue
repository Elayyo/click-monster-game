<template>
    <div id="div">
        <slot></slot>
    </div>

</template>

<script>
export default{}
</script>

<style scoped>
#div{
    border-radius: 5px;
    box-shadow: 10px 5px 5px grey;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin-top: 50px;
    margin-left: 400px;
    margin-right: 400px;
    margin-bottom: 50px;
    gap: 20px;
}
</style>