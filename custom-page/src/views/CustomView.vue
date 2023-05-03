<template>
    <div class="custom">
        <h1>Custom</h1>

      <div class="selection">
        <select class="choose__select" v-model="client">
          <option disabled value="">Choose your client</option>
          <option v-for="client in clients" :key="client.id" :value="client.id">
            {{ client.name }} {{ client.lastname}}
          </option>
        </select>
        <div id="chevrons">
          <i class="fas fa-chevron-up"></i>
          <i class="fas fa-chevron-down"></i>
      </div>
      </div>

      <div class="selection">
      <select class="choose__select" v-model="prestation">
        <option disabled value="">Choose your prestation</option>
        <option v-for="prestation in prestations" :key="prestation.id" :value="prestation.id">
          {{ prestation.name }}
        </option>
      </select>
      <div id="chevrons">
          <i class="fas fa-chevron-up"></i>
          <i class="fas fa-chevron-down"></i>
      </div>
      </div>

      <div class="selection">

      <select class="choose__select" v-model="workflow" @change="workflowLog">
        <option disabled value="">Choose your workflow</option>
        <option v-for="workflow in workflows" :key="workflow.id" :value="workflow.id">
          {{ workflow.name }}
        </option>
        <option value="">none</option>
      </select>
      <div id="chevrons">
          <i class="fas fa-chevron-up"></i>
          <i class="fas fa-chevron-down"></i>
      </div>
      </div>
        

        <div class="custom__content">


          <div v-if="workflowModel">
              <p class="workflow">Workflow choisi : </p>
              <h2 class="worflow">{{ workflows[workflow].name }} </h2>
              <p class="worflow">{{ workflows[workflow].description }} </p>
          </div>

          
          <div class="date">
            <label class="date__label" for="startDate">Date de début</label>
            <input class="date__input" type="date" name="startDate" v-model="startDate">
          </div>
          <div class="date">
            <label class="date__label" for="endDate">Date de fin</label>
            <input class="date__input" type="date" name="endDate" v-model="endDate">
          </div>


          <div class="add__item">
              <i class="fa-solid fa-circle-plus" @click="add"></i>
              <input type="text" placeholder="add an action" v-model="newItem" @keyup.enter="add">
          </div>


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


            <div v-if="workflowModel" >
              <draggable
              tag="ul"
              item-key="id"
              v-model="workflowModel"
              class="vif list-group drop-zone receive-zone"
              v-bind="dragOptions"
              @start="isDragging = true"
              @end="isDragging = false"
              >
                <template #item="{element, index}">
                  <li class="drag-el list-group-item" :aria-label="index">
                      <i class="fa fa-align-justify handle"></i>
                      <div class="item_details">
                      {{items[element.id].title}} 
                      <p>délai : {{ element.delay }} jours</p>
                    </div>
                  </li>
                </template>
              </draggable>
            </div>


            <draggable
              v-else
              tag="ul"
              item-key="id"
              v-model="list"
              class="velse list-group drop-zone receive-zone"
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
                        <input type="number" min="1" class="form-control" placeholder="Veuillez saisir un délai" v-model="element.text" />

                        <i class="fa fa-times close" @click="removeAt(index)"></i>
                      </div>
                    </li>
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
                      <input type="number" min="1" class="form-control" placeholder="Veuillez saisir un délai" v-model="element.text" />

                      <i class="fa fa-times close" @click="removeAt(index)"></i>
                    </div>
                  </li>
                </template>
                
              </draggable>


              <form id="validate">
                <input 
                  type="range" 
                  id="range" 
                  name="ok" 
                  min="0" 
                  max="100" 
                  v-model="vok" 
                  @change="vok==100 ? finish() : '' "
                >
                <br>
                <label 
                  for="ok"
                  id="range-value"
                  class="validate__label"
                  :style="{color: vok==100 ? 'green' : 'red'}"
                >
                  {{ vok==0 ? "slide to validate" : vok==100 ? "validate" : vok }}
                </label>
              </form>
              

<!-- Logo
            <div class="custom__content__logo">
                <img :src="logo" alt="logo" id="logo" @load="convertToWebp">
                <img :src="newLogo" alt="logo">

            </div> -->

        </div>
    </div>
</template>

<script>
import draggable from 'vuedraggable';
import logo from '../assets/images/logo400px.png';
import dbData from '../data/data.json';
import DraggableElement from '../components/svgBloc/ActionElement.vue';


// source : https://learnvue.co/articles/vue-drag-and-drop
// source : https://www.youtube.com/watch?v=-kZLD40d-tI&t=4s
// pour aller plus loin : https://www.youtube.com/watch?v=wWKhKPN_Pmw

export default {
    name: 'CustomView',
    components: {
        draggable,
        DraggableElement,
        },
    display: "Transition",
    order: 6,
    data() {
    return {
      drag: false,
      logo,
      clients: dbData.clients,
      items: dbData.items,
      prestations: dbData.prestations,
      workflows: dbData.workflows,
      SelectedClient:'',
      client: '',
      prestation: '',
      workflow: '',
      newLogo: '',
      listOne: [],
      listTwo: [],
      list: [],
      nestList: [],
      vok: 0,
      newItem: '',
    }
  },
    methods: {
      log() {
        console.log(this.items);
      },
      workflowLog() {
        console.log("index worflows : ", this.workflow);
      },
      removeAt(index) {
      this.list.splice(index, 1);
    },
    finish() {
      console.log('terminado');
      this.vok = 0;
    },
    add() {
      console.log('add tpl');
      console.log(this.items.length);
      if (this.newItem === '') return;
        this.items.push({ 
          "id": this.items.length,
          "title": this.newItem,
          "text": "",
          "delay":0,
          "list": 1,
          "order": 9
        });
        this.newItem = '';
      },


    // function to convert image to webp
    convertToWebp() {
      const img = document.getElementById('logo');
      const canvas = document.createElement('canvas');
      const ctx = canvas.getContext('2d');
      canvas.width = img.width;
      canvas.height = img.height;
      ctx.drawImage(img, 0, 0);
      const dataURL = canvas.toDataURL('image/webp');
      //this.logo = dataURL;
      this.newLogo = dataURL;
    },

  },
    computed: {
      workflowModel() {
        if (this.workflow !== '') {
          return this.workflows[this.workflow].tasks;
        }
        return null;
      },
      dragOptions() {
      return {
        animation: 500,
        group: "actions",
        disabled: false,
        ghostClass: "ghost"
      }
    },
    // listOne() {
    //   return this.items.filter((item) => item.list === 1).sort((a,b)=>a.order <= b.order ? -1 : 1)
    // },
    // listTwo() {
    //   return this.items.filter((item) => item.list === 2).sort((a,b)=>a.order <= b.order ? -1 : 1)
    // },

  },

}
</script>

<style scoped>

h1{
  font-size: 2rem;
  font-weight: bold;
  color: #42b983;
  text-align: center;
}

/* ----------------- */
/* selection element */
/* ----------------- */

*:focus {
  outline: none;
}

select{
  appearance: none;
  width: 100%;
  height: 100%;
  border: none;
  background-color: transparent;
  font-size: 1.25rem;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}



.choose__select {
  display: block;
  margin: 1rem 0 1rem 1rem;
  border-radius: 0.25em;
  padding: 0.25em 0.5em;
  cursor: pointer;
  line-height: 1.1;
  background-color: #fff;
  background-image: linear-gradient(to top, #f9f9f9, #fff 33%);
}

.selection{
  position: relative;
  width: 40%;
}

#chevrons {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  width: 12px;
  padding: 9px;
}

#chevrons i {
  display: block;
  height: 50%;
  color: #d1dede;
  font-size: 0.8rem;
}


@media screen and (max-width: 768px) {
  .selection{
    width: 70%;
    margin: auto;
  }
  .choose__select{
    font-size: 1.25rem;
    line-height: 2;
  }
}

@media screen and (max-width: 480px) {
  select{
  }
  .selection{
    width: 100%;
    margin: auto;
  }
  .choose__select{
    font-size: 1rem;
    line-height: 2;
    margin: 1rem 0 1rem 0;
  }
}



/* ------------- */
/* action button */
/* ------------- */

.custom__content{

  width: 100%;
}

.add__item{
  width: 100%;
  margin: 1rem 0;
  padding: 5px;
  position: relative;
}

.fa-circle-plus{
  color: #42b983;
  font-size: 1.5rem;
  position: absolute;
  top: 50%;
  left: 5px;
  transform: translateY(-50%);
}
.add__item input{
  margin-left: 2rem;
  background-color: transparent;
  font-size: 1.25rem;
  border-radius: 5px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}

.date{
  margin: 1rem 0;
  padding: 5px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: center;
}

.date__label{
  width: 50%;
  font-size: 1.25rem;
  font-weight: bold;
  color: #777;
}
.date__input{
  width: 40%;
  padding: 5px;
  background-color: transparent;
  font-size: 1.25rem;
  border-radius: 5px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}



/* ----------------- */
/* draggable element */
/* ----------------- */

.drop-zone {
    background-color: #eee;
    margin-bottom: 10px;
}
.symbol {
    float: left;
    text-align: center;
    font-size: 2rem;
}
.action-zone {
    width: 30%;
    float: left;
    height: 100%;
}
.receive-zone {
    width: 65%;
    float: right;
    height: 500px;

}

.canvas-zone{
  width: 100%;
  height: 100%;
  background-color: #f5c748;
  margin-bottom: 10px;
}
.drag-el {
  background-color: #fff;
  margin-bottom: 10px;
  padding: 5px;
  position: relative;
}

table {
  border: 2px solid #42b983;
  border-radius: 3px;
  background-color: #fff;
}

th {
  background-color: #42b983;
  color: rgba(255, 255, 255, 0.66);
  user-select: none;
}

td {
  background-color: #f9f9f9;
}

th,
td {
  min-width: 120px;
  padding: 10px 20px;
}

th.active {
  color: #fff;
}

th.active .arrow {
  opacity: 1;
}

.arrow {
  display: inline-block;
  vertical-align: middle;
  width: 0;
  height: 0;
  margin-left: 5px;
  opacity: 0.66;
}

.arrow.asc {
  border-left: 4px solid transparent;
  border-right: 4px solid transparent;
  border-bottom: 4px solid #fff;
}

.arrow.dsc {
  border-left: 4px solid transparent;
  border-right: 4px solid transparent;
  border-top: 4px solid #fff;
}


[data-draggable="true"]{
  cursor: grab;
}

li[draggable="true"] {
  cursor: grabbing;
}


.form-control{
  width: 100%;
  border: 0;
  font-size: 1rem;
  color: #000;
  padding: 0;
  margin: 0;
  text-align: center;
}


i.close {
  position: absolute;
  right: 0;
  top: 0;
  margin: 5px;
  cursor: pointer;
  font-weight: 800;
}


.flip-list-move,
.sortable-chosen {
  transition: transform 2.5s;
  cursor: grabbing;
}

.no-move {
  transition: transform 0s;
}
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
.list-group {
  min-height: 20px;
}

.handle{
  position: absolute;
  top: 50%;
  left: 5px;
  transform: translateY(-50%);
}



.sortable-chosen.sortable-ghost {
  opacity: 0.5;
  background: #c8ebfb;
  cursor: grabbing;
}

.item_details{
  width: 80%;
  margin-left: 1.5rem;
}

/* workflow */
.worflow{
  width: auto;
  text-align: center;
  color: #42b983;
  font-weight: 600;
  margin: 1rem;
}

h2.worflow{
  font-size: 1.5rem;
}
p.worflow{
  
}








/* ---------------- */
/* range validation */
/* ---------------- */
#validate{
  clear: both;
  margin: 1rem auto;
}

.validate__label {
  position: static;
  width: 100px;
  z-index: 1;
  font: 3rem "Monoton", sans-serif;
  color: #EC7474;
  margin: -5rem 0 2rem;
}

/* barre de progression */
input[type=range] {
  appearance: none;
  -webkit-appearance: none; /* Hides the slider so that custom slider can be made */
  background: transparent; /* Otherwise white in Chrome */
  border: none;
  outline: none;
  /* background-color: #42b983; */
  height: 4rem;
  z-index: 2;
  width: 300px;
  border-radius: 50px;
  box-shadow: inset 3px 3px 5px -1px #000;
}

/* rond d'accroche  : Thumb */
input[type=range]::-webkit-slider-thumb {
  appearance: none;
  -webkit-appearance: none;
  height: 4rem;
  width: 4rem;
  border-radius: 50%;
  background: #f0b208;
  cursor: ew-resize;
    box-shadow: 5px 5px 8px -1px #000;
  transition: box-shadow .3s ease-in-out;
}
  
input[type=range]:hover::-webkit-slider-thumb{  
  background: #f5c748;
  box-shadow: 3px 3px 5px -1px #000;
}
/* 
input[type=range]::-moz-range-thumb {
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  border: 1px solid #000000;
  height: 36px;
  width: 16px;
  border-radius: 3px;
  background: #ffffff;
  cursor: pointer;
} */

/* 
input[type=range]::-ms-thumb {
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  border: 1px solid #000000;
  height: 36px;
  width: 16px;
  border-radius: 3px;
  background: #ffffff;
  cursor: pointer;
} */



/* barre de progression : Track */
/* input[type=range]::-webkit-slider-runnable-track  {
  width: 100%;
  border-radius: 50px;
}   */

/* 
input[type=range]::-moz-range-track {
  width: 100%;
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  background: #3071a9;
  border: 0.2px solid #010101;
  border-radius: 50px;
} */

/* 
input[type=range]::-ms-track {
  width: 100%;
  cursor: pointer;

  background: transparent; 
  border-color: transparent;
  color: transparent;
}   */


 /* global range */
/* input[type=range]:focus {
  outline: none; 
  Removes the blue border. You should probably do some kind of focus styling for accessibility reasons though.
}   */


/* input[type=range]::-ms-fill-upper {
  background: #3071a9;
  border: 0.2px solid #010101;
  border-radius: 2.6px;
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
} */

/* input[type=range]:focus::-ms-fill-lower {
  background: #3071a9;
} */
/* input[type=range]:focus::-ms-fill-upper {
  background: #42b983;
} */


</style>