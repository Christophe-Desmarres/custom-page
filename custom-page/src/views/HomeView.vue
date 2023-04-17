<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import background from '../assets/images/mer.jpg';

</script>

<template>
<div class="home">

    <TheWelcome />
    <div id="cover" :style="{backgroundImage:`url(${background})`}"></div>   
 
    <div class="description">   
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Laudantium quaerat eveniet doloribus vero ducimus reiciendis doloremque tenetur porro iste laborum, molestias, voluptatem ipsam itaque ut aliquam voluptates dolorum ad. Minus?</p>
        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Deleniti tempora distinctio laborum eveniet ad eius dicta pariatur necessitatibus vitae veritatis!</p>
        <br>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsa cum perspiciatis illo dolore necessitatibus suscipit labore, a quia aut culpa autem odit quo sed eaque omnis odio officiis facere saepe assumenda voluptatum tenetur illum repudiandae. Adipisci voluptatibus magnam a numquam porro atque eius officia dolor sit cupiditate asperiores ullam ipsum reprehenderit, est, consequatur beatae pariatur vero provident nisi dicta! Ipsa voluptas doloribus, error vel temporibus amet, qui maxime delectus facilis, iusto quam.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
    </div>

</div>
    
</template>

<style scoped>


.description{
    width: 80%;
    margin: 0 auto;
    font-size: 1.2rem;
    line-height: 2rem;
    color: #484848;
    text-align: justify;
    mix-blend-mode: multiply;
    text-shadow: 1px 1px 10px #fff,
                 -1px -1px 2px #fff;

}

#cover {
    position: fixed;
    left: 0;
    top: 0;
    width: 100vw;
    height: 100%;
    z-index: -1;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    background-attachment: fixed;
    animation: mymove 5s infinite;

}

@keyframes mymove {
  50% {
    scale: 1.02;
}
}




</style>
