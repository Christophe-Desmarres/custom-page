<template>
    <div id="ovale">
        
        <span class="element_name"><input type="number" name="" id=""> {{ dragelmt.name }}</span>
</div>
</template>
<script>
export default {
    props: {
      dragelmt: Object,
      default: () => ({})
    },
 }
</script>

<style scoped>
#ovale {
    width: 80%;
    height: 60px;
    border-radius: 60%;
    background: orange;
    margin: 0.2rem auto;
    position: relative;
}

.element_name{
    width: 100%;
    text-align: center;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

input[type="number"]{
    width: 38px;
    display: inline;
    padding: 0.2rem;
    background: none;
    text-align: center;
}
.times{
  background-color: #00bd7e;
}




</style>
  