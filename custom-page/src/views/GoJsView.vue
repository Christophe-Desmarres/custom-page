<template>
    <div>
        <div id="myDiagramDiv">
            <RectBloc x="100" y="200" backgroundColor="blue" />

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
        }
    },
    methods: {

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