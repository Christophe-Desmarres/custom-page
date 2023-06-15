<script setup>
import HelloWorld from '../components/HelloWorld.vue';

</script>

<template>
<div class="home">

    <div id="cover"></div>   

    <hello-world msg="Bienvenue" class="titre"/>
   
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

    <div id="about_page">
        <div class="about">
            <h2>Vue.js</h2>
            <p>
            Vue.js est un framework JavaScript progressif et réactif utilisé pour la création d'interfaces utilisateur (UI) complexes et interactives. Il est souvent comparé à d'autres frameworks populaires tels que React et Angular.
            <br>
            Le principal avantage de Vue.js est sa simplicité et sa facilité d'utilisation. Son API intuitive et sa documentation claire permettent aux développeurs de créer des applications web robustes et réactives en un temps record. Le framework met l'accent sur la composition de composants réutilisables, qui permettent de créer des interfaces utilisateur riches et modulaires.
            <br>
            Vue.js se concentre sur la réactivité, ce qui signifie que les modifications apportées à l'état de l'application sont immédiatement reflétées dans l'interface utilisateur. Il utilise une structure de données appelée "Vue instance" qui facilite la gestion de l'état de l'application.
            <br>
            Enfin, Vue.js est très flexible et peut être intégré facilement avec d'autres bibliothèques et frameworks. Cela signifie que les développeurs peuvent utiliser Vue.js pour construire des interfaces utilisateur de manière modulaire et évolutive, en fonction des besoins spécifiques de leur projet.
            <br>
            En somme, Vue.js est un framework JavaScript moderne, simple, réactif et flexible, qui offre des outils puissants pour la création d'interfaces utilisateur riches et modulaires.
            <br>
            </p>
            <em>- ChatGPT Mar 23 Version -</em>
        </div>
        <div class="about">
            <h2>Workflow</h2>
            <p>
            Un workflow est une séquence d'activités liées et organisées, effectuées par des personnes ou des systèmes, dans le but de produire un résultat ou une sortie spécifique. Les workflows sont souvent utilisés dans les entreprises pour automatiser les processus de travail et augmenter l'efficacité des opérations.
            <br>
            Un workflow typique peut comporter plusieurs étapes, chacune ayant son propre ensemble de tâches et d'actions à réaliser. Les workflows peuvent être simples ou complexes, en fonction des besoins de l'entreprise. Par exemple, un workflow simple peut être utilisé pour suivre le processus de création d'un document, tandis qu'un workflow complexe peut être utilisé pour coordonner une équipe de développement de logiciels.
            <br>
            Les workflows peuvent être manuels ou automatisés. Dans un workflow manuel, les tâches sont effectuées par des humains, souvent en utilisant des formulaires ou des feuilles de calcul. Dans un workflow automatisé, les tâches sont effectuées par des systèmes informatiques, qui sont programmés pour effectuer des tâches spécifiques en fonction des entrées fournies par les utilisateurs.
            <br>
            En somme, les workflows sont un outil précieux pour l'automatisation et l'optimisation des processus de travail. Ils permettent d'organiser les activités de manière logique et de maximiser l'efficacité des opérations. Les workflows peuvent être utilisés dans de nombreux domaines, tels que la gestion de projet, la production, les finances et bien d'autres.
        </p>
            <em>- ChatGPT Mar 23 Version -</em>
        </div>
    </div>

</div>
    
</template>

<style scoped>



#cover {
    position: fixed;
    left: 0;
    top: 0;
    width: 100vw;
    height: 100%;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    background-attachment: fixed;
    animation: mymove 5s infinite;
    background-image: url('../assets/images/mer.jpg');
}

@keyframes mymove {
  50% {
    scale: 1.02;
}
}

.titre {
  height: 1.5em;
  margin: 2rem auto;
  mix-blend-mode: multiply;
}
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


.description p q::before{
    content: "„";
    font-weight: 600;
    font-size: 1.5rem;
}

.description p q::after{
    content: "“";
    font-weight: 600;
    font-size: 1.5rem;
}

.description p em {
    font-style: italic;
}


.about {
    width: 70%;
    padding: 2rem;
    margin: 2rem auto;
    border: 1px solid #ccc;
    border-radius: 5px;
    color: #2c3e50;
    box-shadow: 0 0 10px #14141433;
    counter-increment: about;
    mix-blend-mode: multiply;
  }

  .about h2 {
    font-size: 2rem;
    margin-bottom: 1rem;
    text-align: center;
  }

  .about em::after{
    content: "#article_counter " counter(about);
    margin: 0.5rem 0;
    font-size: 0.7rem;
    font-style: italic;
    float: right;
  }

  .about p {
    font-weight: 500;
    line-height: 1.2rem;
    margin-bottom: 1rem;
    text-align: justify;
  }

  .about em {
    font-style: italic;
}

@media screen and (max-width: 400px) {
  #about_page {
    width: 100%;
  }
  .about {
    width: 90%;
    margin: 2rem auto;
    padding: 0.5rem;
    border: none;
    border-bottom: 2px solid #33333333;
    box-shadow: none;
  }
}




</style>
