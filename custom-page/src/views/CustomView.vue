<template>
    <div class="custom">
        <h1>Custom</h1>
        <div class="custom__content">

            <div
                class="drop-zone action-zone"
                @drop="onDrop($event, 1)"
                @dragover.prevent
                @dragenter.prevent>

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
                    <div
                        class="drag-el"
                        v-for="item in listTwo"
                        :key="item.title"
                        draggable="true"
                        @dragstart="startDrag($event, item)"
                        >
                        <input type="text" v-model="item.title">
                       
                    </div>                
            </div>

        </div>
    </div>
</template>

<script>
// source : https://learnvue.co/articles/vue-drag-and-drop
// source : https://www.youtube.com/watch?v=-kZLD40d-tI&t=4s
// pour aller plus loin : https://www.youtube.com/watch?v=wWKhKPN_Pmw

export default {
    name: 'Custom',
    data() {
    return {
      items: [
        {
          id: 0,
          title: 'input A',
          list: 1,
        },
        {
          id: 1,
          title: 'input B',
          list: 1,
        },
        {
          id: 2,
          title: 'input C',
          list: 1,
        },
        {
          id: 3,
          title: 'input D',
          list: 1,
        },
      ],
    }
  },
    methods: {
    startDrag(evt, item) {
        console.log(evt)
      evt.dataTransfer.dropEffect = 'move'
      evt.dataTransfer.effectAllowed = 'move'
      evt.dataTransfer.setData('itemID', item.id)
    },
    onDrop(evt, list) {
        console.log(evt)

      const itemID = evt.dataTransfer.getData('itemID')
      const item = this.items.find((item) => item.id == itemID)
      item.list = list
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
</style>