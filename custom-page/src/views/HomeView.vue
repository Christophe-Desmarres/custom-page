<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import background from '../assets/images/mer.jpg';

</script>

<template>
<div class="home">

    <TheWelcome />
    <div id="cover" :style="{backgroundImage:`url(${background})`}"></div>   
 
    <div class="description">   
        <p>
            <q>
                Ce projet consiste en une application web permettant à l'utilisateur de créer des processus en utilisant des blocs prédéfinis et de les connecter entre eux en utilisant des fils. Les blocs peuvent être déplacés et positionnés à l'aide de la souris, ce qui rend la création de workflows facile et intuitive.
                <br>
                Le développement de cette application a été réalisé en utilisant Vue.js, un framework JavaScript progressif et réactif. Les composants "drag and drop" ont été créés à l'aide de la bibliothèque de glisser-déposer de Vue.js, qui permet de créer facilement des éléments interactifs et dynamiques.
                <br>
                L'interface utilisateur de l'application est conçue de manière à faciliter la création de workflows complexes. Les utilisateurs peuvent facilement ajouter des blocs à leur processus, les connecter entre eux et définir des actions à effectuer lors de l'exécution du workflow. L'application est également dotée de fonctionnalités avancées telles que la possibilité de visualiser et de modifier les workflows existants, ainsi que de les partager avec d'autres utilisateurs.
                <br>
                En somme, ce projet de développement web réalisé avec Vue.js pour la création de workflows en utilisant des composants "drag and drop" est une solution pratique, rapide et facile à utiliser pour la création de processus de travail automatisés.
            </q>
            <br>
            <em>- ChatGPT Mar 23 Version -</em>
        </p>
    </div>

</div>
    
</template>

<style scoped>


.description{
    width: 80%;
    margin: 0 auto 2rem;
    font-size: 1.2rem;
    line-height: 1.7rem;
    color: #484848;
    text-align: justify;
    mix-blend-mode: multiply;
    text-shadow: 1px 1px 10px #fff,
                 -1px -1px 2px #fff;
}


q::before{
    content: "„";
    font-weight: 600;
    font-size: 1.5rem;
}

q::after{
    content: "“";
    font-weight: 600;
    font-size: 1.5rem;
}

em{
    font-style: italic;
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
