<template>
    <div>
        <h1>CanvasSvgVue</h1>
        <p>Drag and drop elements from the left to the right</p>
      <ul style="color: red;marginBottom:2rem;">// TODO
        <li><input type="checkbox" checked> créer des rectangles avec texte pour les actions</li>
        <li><input type="checkbox" checked> créer des types (actions, temps, conditions)</li>
        <li><input type="checkbox" checked> créer des formes pour chaque type (actions, temps, conditions)</li>
        <li><input type="checkbox" checked> afficher la liste des actions à gauche</li>
        <li><input type="checkbox" checked> afficher la liste des actions dans le "canvas" à droite</li>
        <li><input type="checkbox" checked> drag and drop vers le "canvas"</li>
        <li><input type="checkbox"> fct lors du focus</li>
        <li><input type="checkbox"> fct lors du drag</li>
        <li><input type="checkbox"> fct lors du mvt</li>
        <li><input type="checkbox"> fct lors du drop</li>
        <li><input type="checkbox"> créer des actions perso</li>
      </ul>

      <custom-block msg="Custom bloc" />

      <input type="radio" id="actions" value="actions" v-model="type" />
      <label for="actions">actions</label>

      <input type="radio" id="times" value="times" v-model="type" />
      <label for="times">times</label>

      <input type="radio" id="conditions" value="conditions" v-model="type" />
      <label for="conditions">conditions</label>



      <div class="dragdrop-zone">
        
        <div class="zone">
      <p class="drop-title">Drag in this list</p>

        <draggable 
              class="list-group drop-zone action-zone"
              :class="type === 'conditions' ? 'conditions' : (type === 'times') ? 'times' :  'items' "
              tag="ul"
              item-key="id"
              v-model="type" 
              :list="((type=== 'conditions') ? conditions : (type === 'times') ? times :  items )"
              :group="{ name: 'actions', pull: 'clone', put: false }"
              @change="log"
              >
                <template #item="{element}">
                  <draggable-element :dragelmt="element" />
                </template>
            </draggable>

            

          </div>
            <div class="zone">

            <p class="drop-title">Drop in this box</p>

        <draggable
              tag="ul"
              item-key="id"
              v-model="list"
              class="velse svg-zone list-group drop-zone receive-zone"
              v-bind="dragOptions"
              @start="isDragging = true"
              @end="isDragging = false"
              >

                <template #item="{element, index}">
                  <li :class="element.type">
                      <ActionElement :dragelmt="element" v-if="element.type == 'items'"/>
                      <TimeElement  :dragelmt="element" v-if="element.type == 'times'"/>
                      <condition-element :dragelmt="element" v-if="element.type == 'conditions'"/>
                      <div class="line">{{ index }}</div>
                </li>
                </template>
                
              </draggable>
            </div>
              </div>
            
    </div>
</template>

<script>
// à creuser
// source : https://codepen.io/unicurva/pen/MbRYqg?editors=0110
import draggable from 'vuedraggable';
import DraggableElement from '../components/svgBloc/DraggableElement.vue';
import dbData from '../data/data.json';
import CustomBlock from '../components/svgBloc/CustomBlock.vue';
import ActionElement from '../components/svgBloc/ActionElement.vue';
import TimeElement from '../components/svgBloc/TimeElement.vue';
import ConditionElement from '../components/svgBloc/ConditionElement.vue';


export default {
    name: 'CanvasSvgView',
    components: {
        draggable,
        DraggableElement,
        CustomBlock,
        ActionElement,
        TimeElement,
        ConditionElement,
        },
    data() {
        return {
        drag: false,
        items: dbData.items,
        prestations: dbData.prestations,
        workflows: dbData.workflows,
        times: dbData.times,
        conditions: dbData.conditions,
        list: '',
        type: 'actions',
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

#selected_element{
  width: 75%;
  display: block;
  margin: 1rem 0;
  padding: 0.5rem;
  background-color: #fff;
  box-shadow: 0 0 3px #333;
}

.dragdrop-zone{
  width: 100%;
  box-shadow: 0 0 3px #333;
  margin: 1rem 0;
  display: flex;
  user-select: none;
}

.zone{
  width: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* zone pour choisir les éléments */
.action-zone{
  width: 75%;
  background-color: #f5c74830;
  box-shadow: 0 0 3px #333;
  margin: 1rem 0;
  padding: 0.5rem;
}
.action-zone li{
  list-style: none;
  margin: 0.5rem 0;
  padding: 0.5rem;
  background-color: #fff;
  box-shadow: 0 0 3px #333;
  cursor: grab;
}

/* zone pour construire les suites d'éléments */
.canvas-zone{
  width: 50%;
  background-color: #f5c74830;
  box-shadow: 0 0 3px #333;
  margin: 1rem 0;
}

.drop-title{
  width: 50%;

  font-weight: 600;
  text-align: center;
  margin: 1rem 0;
}
.svg-zone{
  width: 75%;
  min-height: 2rem;
  background-color: #f5c74830;
  box-shadow: 0 0 3px #333;
  margin: 1rem 0;
  padding: 0.5rem;
}
.svg-zone li{
  width:100%;
  list-style: none;
  margin: auto;
  cursor: grab;
}

.line{
  position:relative;
  height: 1rem;
}
.line::after{
  position:absolute;
  content:'|';
  left:50%;
  transform: translateX(-50%);
}

svg:hover{
  cursor: grab;
}

svg:active{
  cursor: grabbing;
}

svg:focus{
  cursor: grabbing;
}


/* canvas zone */
svg {
  box-sizing: border-box;
  border: 1px solid rgb(212, 212, 212);
}

circle {
  stroke: rgb(95, 176, 228);
  stroke-width: 2;
  fill: rgba(205, 246, 255, 0.3);
}

line {
  stroke: rgb(212, 212, 212);
  stroke-width: 1px;
  shape-rendering: crispEdges;
}

</style>