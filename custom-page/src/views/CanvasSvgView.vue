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
              tag="canvas"
              item-key="id"
              v-model="list"
              class="velse list-group drop-zone canvas-zone"
              v-bind="dragOptions"
              @start="isDragging = true"
              @end="isDragging = false"
              >
                <template #item="{element, index}">
                  <li class="drag-el list-group-item">
                    <div class="item_details">
                      <i
                        :class="element.fixed ? 'fa fa-anchor' : 'glyphicon glyphicon-pushpin'"
                        @click="element.fixed = !element.fixed"
                        aria-hidden="true"
                      ></i>
                      {{ index }} 
                      <i class="fa fa-align-justify handle"></i>
                      {{element.title}} 
                    </div>
                  </li>
                </template>
                
              </draggable>

              <!-- <draggable-element /> -->

    </div>
</template>

<script>
import draggable from 'vuedraggable';
import DraggableElement from '../components/DraggableElement.vue';
import dbData from '../data/data.json';

export default {
    name: 'CanvasSvgView',
    components: {
        draggable,
        DraggableElement,
        },
    data() {
        return {
        drag: false,
        items: dbData.items,
        prestations: dbData.prestations,
        workflows: dbData.workflows,
        list: [],

        }
    },
    
    methods: {
      log() {
        console.log(this.items);
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
  height: 100%;
  background-color: #f5c748;
  margin-bottom: 10px;
}

</style>