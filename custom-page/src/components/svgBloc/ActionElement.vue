<template>
             <div id="action">
                <div class="rect"></div>
                <span class="element_name">{{ dragelmt.name }}</span>
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

#action{
    width: 80%;
    height: 30px;
    margin: 0.2rem auto;
    position: relative;
}

.rect{
    /* position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%); */
    width: 100%;
    height: 100%;
    margin: auto;
    background: red;
    opacity:0.5;
    border-radius: 5px;
    border: 2px solid black;
  /* height: fit-content; */
  /* overflow: hidden; */
}


.element_name{
    width: 100%;
    text-align: center;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

</style>
  