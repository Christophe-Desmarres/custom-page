<template>
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
    <h2>Vuedraggable</h2>
    <p>
      vuedraggable est une bibliothèque de composants Vue.js qui permettent de créer des interfaces utilisateur interactives de type glisser-déposer. Cette bibliothèque permet aux développeurs de créer des fonctionnalités glisser-déposer complexes en utilisant des composants simples et réutilisables.
      <br>
      vuedraggable offre une grande flexibilité dans la création d'interfaces utilisateur, en permettant aux utilisateurs de déplacer des éléments à l'intérieur d'une liste, de les déplacer d'une liste à l'autre, et même de trier les éléments selon différents critères. Cette bibliothèque est également compatible avec les bibliothèques de composants les plus populaires, telles que Bootstrap et Materialize.
      <br>
      En outre, vuedraggable est facile à utiliser et peut être personnalisé en fonction des besoins spécifiques de chaque projet. Il est également très performant, ce qui en fait une excellente option pour les projets exigeants en termes de performances.
      <br>
      En somme, vuedraggable est une bibliothèque de composants Vue.js très utile pour la création d'interfaces utilisateur interactives et flexibles en utilisant des fonctionnalités glisser-déposer. Elle offre des fonctionnalités avancées, une grande flexibilité et une excellente performance, ce qui en fait un outil de choix pour les développeurs qui souhaitent créer des interfaces utilisateur efficaces et interactives.
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
</template>

<style scoped>

 .about {
    width: 70%;
    padding: 2rem;
    margin: 2rem auto;
    border: 1px solid #ccc;
    border-radius: 5px;
    color: #2c3e50;
    box-shadow: 0 0 10px #14141433;
    counter-increment: about;
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

  p {
    margin-bottom: 1rem;
    text-align: justify;
  }

  em{
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
