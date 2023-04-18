<template>
    <div class="custom">
        <h1>Custom</h1>


      <select v-model="client">
        <option v-for="client in clients" :key="client.id" :value="client.id">
          {{ client.name }} {{ client.lastname}}
        </option>
      </select>

      <select v-model="prestation">
        <option v-for="prestation in prestations" :key="prestation.id" :value="prestation.id">
          {{ prestation.name }}
        </option>
      </select>
        

        <div class="custom__content">



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
                <li class="drag-el list-group-item">
                  <i class="fa fa-align-justify handle"></i>
                  {{element.title}}
                </li>
              </template>
            </draggable>






            
            
            <draggable
            tag="ul"
            item-key="id"
            v-model="list"
            class="list-group drop-zone receive-zone"
            v-bind="dragOptions"
            @start="isDragging = true"
            @end="isDragging = false"
            >
            
            <template #item="{element, index}">
                <li class="drag-el list-group-item">
                  <i
              :class="
                element.fixed ? 'fa fa-anchor' : 'glyphicon glyphicon-pushpin'
              "
              @click="element.fixed = !element.fixed"
              aria-hidden="true"
            ></i>
                  {{ index }} 
                  <i class="fa fa-align-justify handle"></i>
                  {{element.title}} 
                  <input type="number" min="1" class="form-control" v-model="element.text" />

                  <i class="fa fa-times close" @click="removeAt(index)"></i>
                
                </li>
                </template>
                
              </draggable>

              <form >
                <input 
                type="range" 
                id="range" 
                name="ok" 
                min="0" 
                max="100" 
                v-model="vok" 
                @change="vok==100 ? finish() :handleMouseMove() "
                >
                <br>
                <label 
                for="ok"
                id="range-value"
                >{{ vok==0 ? "slide to unlock" : vok==100 ? "terminado" : vok }}</label>
              </form>
              

<!-- TAB view
            <div                 
                class="drop-zone receive-zone"
                @drop="onDrop($event, 2)"
                @dragover.prevent
                @dragenter.prevent>
                workflow

                <table>
                    <tr>
                        <th>check</th>
                        <th>action</th>
                        <th>info</th>

                    </tr>



                    <tr
                        class="drag-el"
                        v-for="item in listTwo"
                        :key="item.title"
                        draggable="true"
                        @dragstart="startDrag($event, item)"
                        >
                                <td>
                                    <input type="checkbox" v-model="item.checked">
                                </td>
                                <td>
                                    {{ item.title }}
                                </td>
                                <td>
                                  <div v-for="(info, index) in item.info" :key="info" :value="info">
                                    {{ clients[client].name }}<br>
                                    {{ prestations[prestation].name }}<br>
                                  </div>
                                </td>
                          </tr>                
                        </table>
            </div> -->

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


// source : https://learnvue.co/articles/vue-drag-and-drop
// source : https://www.youtube.com/watch?v=-kZLD40d-tI&t=4s
// pour aller plus loin : https://www.youtube.com/watch?v=wWKhKPN_Pmw

export default {
    name: 'Custom',
    components: {
            draggable,
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
      SelectedClient:'',
      client: '',
      prestation: '',
      newLogo: '',
      listOne: [],
      listTwo: [],
      list: [],
      nestList: [],
      vok: 0,
    }
  },
    methods: {
      log() {
        console.log(this.items);
      },
      removeAt(idx) {
      this.list.splice(idx, 1);
    },
    finish() {
      alert('terminado')
    },
    handleMouseMove() {
      const rangeValueElement = document.querySelector("#range-value")
      const inputElement = document.querySelector('input[type="range"]')
      const fillAreaElement = document.querySelector(".fill-area")
      
      const hueRotate = "hue-rotate(" + this.vok + "deg)"
      
      rangeValueElement.textContent = this.vok
      rangeValueElement.style.filter = hueRotate
      
      inputElement.style.filter = hueRotate
      
      fillAreaElement.style.left = this.vok + "vw"
      fillAreaElement.style.width = (100-this.vok) + "vw"
      fillAreaElement.style.filter = hueRotate
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
.drop-zone {
    background-color: #eee;
    margin-bottom: 10px;
    padding: 10px;
}
.symbol {
    float: left;
    text-align: center;
    font-size: 2rem;
}
.action-zone {
    width: 20%;
    height: 600px;
    float: left;
}
.receive-zone {
    width: 70%;
    height: 600px;
    float: right;
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



.sortable-chosen.sortable-ghost {
  opacity: 0.5;
  background: #c8ebfb;
  cursor: grabbing;
}

label {
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
  height: 2rem;
  z-index: 2;
  width: 50vw;
  border-radius: 100vmax;
  box-shadow: inset 3px 3px 5px -1px #000;
}

/* rond d'accroche  : Thumb */
input[type=range]::-webkit-slider-thumb {
  appearance: none;
  -webkit-appearance: none;
  height: 2rem;
  width: 2rem;
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