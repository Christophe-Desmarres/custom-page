<template>
    <div>
        <div 
        id="canvas"
        @click="origin"        
        >
          <RectBloc v-for="shape in shapes.filter(shape=>shape.type==='rectangle')" v-bind="shape" :key="shape.id" @mousedown="changeXY($event,shape.x,shape.y)"/>
          <RoundBloc v-for="shape in shapes.filter(shape=>shape.type==='round')" v-bind="shape" :key="shape.id" @mousedown="changeXY($event,shape.x,shape.y)"/>
          <DiamondBloc v-for="shape in shapes.filter(shape=>shape.type==='losange')" v-bind="shape" :key="shape.id" @mousedown="changeXY($event,shape.x,shape.y)"/>

        </div>
        <div id="myPaletteDiv">
            <div id="form1" class="palette__form square draggable" style="background-color: greenyellow;"></div>
            <div id="form2" class="palette__form rect draggable" style="background-color: aquamarine;"></div>
            <div id="form3" class="palette__form losange draggable" style="background-color: bisque;"></div>
            <div id="form4" class="palette__form round draggable" style="background-color: blueviolet;"></div>
            <div id="form4" class="palette__form ellipse draggable" style="background-color: orange;"></div>

        </div>
        <div id="mySavedModel"><button>sauvegarder</button>
          <ul>
            <li><input type="checkbox" checked />afficher une selection de formes</li>
            <li><input type="checkbox"  />drag&drop les formes de la selection vers le canvas</li>
            <li><input type="checkbox"  />déplacer les formes vers le canvas</li>
            <li><input type="checkbox"  />afficher les formes dans le canvas</li>
            <li><input type="checkbox" checked />déplacer les formes du canvas</li>
            <li><input type="checkbox"  />agrandir les formes du canvas</li>
            <li><input type="checkbox"  />créer des liens entre les formes du canvas</li>
            <li><input type="checkbox"  />modifier le contenu ou la couleur des formes</li>
            <li><input type="checkbox"  />charger les formes</li>
            <li><input type="checkbox"  />supprimer les formes</li>
            <li><input type="checkbox"  />sauvegarder les formes</li>

          </ul>
        </div>
    </div>
</template>

<script>
import RectBloc from '../components/htmlBloc/RectBloc.vue'
import RoundBloc from '../components/htmlBloc/RoundBloc.vue'
import DiamondBloc from '../components/htmlBloc/DiamondBloc.vue'

export default {
    name: 'GoJsView',
    components: {
        RectBloc,
        RoundBloc,
        DiamondBloc

        },
    data() {
        return {
          shapes:[
            {
              type:"rectangle",
              id:1,
              x: 70,
              y: 150,
              width: 100,
              height: 100,
              backgroundColor: 'greenyellow',
              message:"Hello"
            },
            {
              type:"rectangle",
              id:2,
              x: 250,
              y: 150,
              width: 75,
              height: 125,
              backgroundColor: 'aquamarine',
              message:"rect"
            },
            {
              type:"losange",
              id:3,
              x: 430,
              y: 150,
              width: 90,
              height: 90,
              backgroundColor: 'bisque',
              message:"diamond"
            },
            {
              type:"round",
              id:4,
              x: 610,
              y: 150,
              width: 100,
              height: 100,
              backgroundColor: 'blueviolet',
              message:"the ring"
            },
            ]
        }
    },
    methods: {
        changeXY(e,x,y) {
          // console.log(e.target.id)
          // console.log(e.offsetX, e.offsetY)
        },
        origin(e) {
          console.log(e.target.id)
          if (e.target.id === "canvas") {
            let allSelected = document.querySelectorAll('.selected');
            allSelected.forEach((element) => {
              element.classList.remove('selected');
            });
          }
        }

    },
    computed: {

    },
}
</script>

<style scoped>
    #canvas {
        border: solid 1px black;
        width:90%;
        height:600px;
        position: relative;
        overflow: hidden;
    }
    #myPaletteDiv {
        border: solid 1px black;
        width:90%;
        height:100px;
        display: flex;
    }

    .palette__form{
        width: 50px;
        height: 50px;
        margin: auto 1rem;
        display: inline-block;
        border: solid 1px black;
        cursor: move;
    }

    .square{
        width: 50px;
        height: 50px;
      }
    .rect{
      width: 70px;
    }

    .losange{
        width: 40px;
        height: 40px;
        transform: rotate(45deg);
    }

    .round{
        border-radius: 50%;
    }

    .ellipse{
        border-radius: 50%;
        width: 70px;
        height: 50px;
    }



    #mySavedModel {
      width:90%;
      height:100%;
      display: flex;
      }

    #mySavedModel button {
      width: 50%;
      padding: 1rem;
      margin: 1rem auto;
      color: #333;
      font-size: 2rem;
      font-weight: 600;
      border: solid 2px #333;
      border-radius: 15px;
      background: greenyellow;
      transition: all 0.3s ease-in-out;
    }

    #mySavedModel button:hover {
      color: greenyellow;
      background: #333;
      border-color: greenyellow;
    }

    #mySavedModel button:active {
      transform: scale(0.98);
    }

    #mySavedModel button:focus {
      outline: none;
    }



</style>