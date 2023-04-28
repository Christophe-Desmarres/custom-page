<template>
    <div>
        <h1>CanvasSvgVue</h1>
        <p>CanvasSvgVue</p>

      <ul style="color: red;">// TODO
        <li>- créer des rectangles svg avec texte pour les actions</li>
        <li>- afficher la liste des actions à gauche</li>
        <li>- afficher la liste des actions dans le canvas à droite</li>
        <li>- drag and drop vers le canvas</li>
        <li>- fct lors du focus</li>
        <li>- fct lors du drag</li>
        <li>- fct lors du mvt</li>
        <li>- fct lors du drop</li>
        <li>- créer des actions perso</li>
      </ul>

      <custom-block msg="Custom" />

        
        <draggable 
              class="list-group drop-zone action-zone"
              tag="ul"
              item-key="id"
              v-model="items" 
              :list="items"
              :group="{ name: 'actions', pull: 'clone', put: false }"
              @change="log"
              >
                <template #item="{element}">
                  <draggable-element :dragelmt="element" />
                </template>
            </draggable>

        
        <draggable
              tag="ul"
              item-key="id"
              v-model="items"
              class="velse list-group drop-zone receive-zone"
              v-bind="dragOptions"
              @start="isDragging = true"
              @end="isDragging = false"
              >
                <template #item="{element, index}">
                  <li>
                  <svg height="30" width="auto">
                    <text 
                      y="12" 
                      x="0"
                      >
                      {{ index }} - {{ element.title }}
                    </text>
                  </svg>
                </li>
                </template>
                
              </draggable>

              <!-- <draggable-element /> -->

              <canvas class="canvas-zone">

              </canvas>




    </div>
</template>

<script>
import draggable from 'vuedraggable';
import DraggableElement from '../components/DraggableElement.vue';
import dbData from '../data/data.json';
import CustomBlock from '../components/CustomBlock.vue';

export default {
    name: 'CanvasSvgView',
    components: {
        draggable,
        DraggableElement,
        CustomBlock,
        },
    data() {
        return {
        drag: false,
        items: dbData.items,
        prestations: dbData.prestations,
        workflows: dbData.workflows,
        list: this.items,

        }
    },
    
    methods: {
      log() {
        console.log(this.items);
      },
      // to create text canvas
      createText(index) {
        console.log(index);
        // var canvas = document.getElementById("myCanvas");
        // var ctx = canvas.getContext("2d");
        // ctx.font = "30px Arial";
        // ctx.strokeText("Hello World",10,50);
      },
    },
    computed: {
      dragOptions() {
      return {
        animation: 500,
        group: "actions",
        disabled: false,
        ghostClass: "ghost"
      }
    },
    },
}
</script>

<style scoped>

.canvas-zone{
  width: 100%;
  /* background-color: #f5c748; */
  box-shadow: 0 0 3px #333;
  margin: 1rem 0;
  position: relative;
}

svg{
  background-color: #f5c748;
  box-shadow: 0 0 3px #333;
  margin-bottom: 10px;
  height: fit-content;
}

</style>