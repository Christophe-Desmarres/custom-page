<template>
    <div id="condition">

        <div id="losangeh">
        </div>
        <div id="losangeb">
        </div>
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

#condition{
    position: relative;

}
#losangeh{
    margin: auto;
	width: 0;
	height: 0;
	border-left: 100px solid transparent;
	border-right: 100px solid transparent;
	border-bottom: 25px solid #069;
}

#losangeb{
    margin: auto;
	width: 0;
	height: 0;
	border-left: 100px solid transparent;
	border-right: 100px solid transparent;
	border-top: 25px solid #069;
}
/* 

.losange:before{
	content:'';
	border: 1px solid #069;
	border-left: 100px solid transparent;
	border-right: 100px solid transparent;
	border-top: 25px solid #069;
	width:0;
	height:0;
	position: absolute;
	top:25px;
	left:-100px;
} */


.element_name{
    width: 100%;
    text-align: center;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: aliceblue;
    font-weight: 600;
}

</style>
  