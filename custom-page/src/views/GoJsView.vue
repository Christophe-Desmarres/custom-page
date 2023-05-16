<template>
    <div>
        <div 
        id="canvas"
        @click="origin"        
        >
            <RectBloc v-bind="rectangle1"/>
            <RectBloc v-bind="rectangle2"/>

        </div>
        <div id="myPaletteDiv">
            <div id="form1" class="palette__form rect draggable" style="background-color: greenyellow;"></div>
            <div id="form2" class="palette__form rect draggable" style="background-color: aquamarine;"></div>
            <div id="form3" class="palette__form losange draggable" style="background-color: bisque;"></div>
            <div id="form4" class="palette__form round draggable" style="background-color: blueviolet;"></div>

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

export default {
    name: 'GoJsView',
    components: {
        RectBloc

        },
    data() {
        return {
         rectangle1: {
            id:1,
            x: 70,
            y: 150,
            width: 100,
            height: 100,
            backgroundColor: 'greenyellow',
            message:"Hello"
          },
          rectangle2: {
            id:2,
            x: 250,
            y: 150,
            width: 100,
            height: 100,
            backgroundColor: 'aquamarine',
            message:""
          },
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

    .rect{

    }

    .losange{
        width: 40px;
        height: 40px;
        transform: rotate(45deg);
    }

    .round{
        border-radius: 50%;
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