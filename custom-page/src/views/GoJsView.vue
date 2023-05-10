<template>
    <div>
        <div id="myDiagramDiv">
            <RectBloc id="rectangle1" v-bind="rectangle1" @click="changeXY" />
            <RectBloc id="rectangle2" v-bind="rectangle2"  @click="changeXY" />

        </div>
        <div id="myPaletteDiv"></div>
        <div id="mySavedModel"><button>sauvegarder</button></div>
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
            x: 70,
            y: 150,
            width: 100,
            height: 100,
            backgroundColor: 'greenyellow',
            message:"Hello"
          },
          rectangle2: {
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
          console.log(e.target.id)
          console.log(e.offsetX, e.offsetY)

        }

    },
    computed: {

    },
}
</script>

<style scoped>
    #myDiagramDiv {
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