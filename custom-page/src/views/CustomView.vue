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

            <div
                class="drop-zone action-zone"
                @drop="onDrop($event, 1)"
                @dragover.prevent
                @dragenter.prevent>
                Action
                <div v-for="item in listOne" 
                :key="item.title" 
                class="drag-el"
                draggable="true"
                @dragstart="startDrag($event, item)"

                >
                    {{ item.title }}
                </div>
            </div>
            <div class="symbol">
                &#171;&#61;&#187;
            </div>


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
            </div>

            
            <div class="custom__content__logo">
                <img :src="logo" alt="logo" id="logo" @load="convertToWebp">
                <img :src="newLogo" alt="logo">

            </div>

        </div>
    </div>
</template>

<script>
import logo from '../assets/images/logo400px.png';
import dbData from '../data/data.json';


// source : https://learnvue.co/articles/vue-drag-and-drop
// source : https://www.youtube.com/watch?v=-kZLD40d-tI&t=4s
// pour aller plus loin : https://www.youtube.com/watch?v=wWKhKPN_Pmw

export default {
    name: 'Custom',
    data() {
    return {
      logo,
      clients: dbData.clients,
      items: dbData.items,
      prestations: dbData.prestations,
      SelectedClient:'',
      client: '',
      prestation: '',
      newLogo: '',



    }
  },
    methods: {
    startDrag(evt, item) {
      console.log('je prends la case "'+ evt.srcElement.__vnode.key + '"')
      // console.log(evt)
      evt.dataTransfer.dropEffect = 'move'
      evt.dataTransfer.effectAllowed = 'move'
      evt.dataTransfer.setData('itemID', item.id)
    },

    onDrop(evt, list) {
      console.log('je pose')
      // console.log(evt)
      const itemID = evt.dataTransfer.getData('itemID')
      const item = this.items.find((item) => item.id == itemID)
      item.list = list
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
    listOne() {
      return this.items.filter((item) => item.list === 1)
    },
    listTwo() {
      return this.items.filter((item) => item.list === 2)
    },

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
}

table {
  border: 2px solid #42b983;
  border-radius: 3px;
  background-color: #fff;
}

th {
  background-color: #42b983;
  color: rgba(255, 255, 255, 0.66);
  cursor: pointer;
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
</style>