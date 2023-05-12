<template>
  <div       
    class="rect"
    :style="{ width: startWidth + 'px', height: startHeight + 'px', backgroundColor: backgroundColor, position: 'absolute', left: startX + 'px', top: startY + 'px', cursor: dragging ? 'move' : 'default' }"
    @click="onClick"
    @mousedown="startDragging"
    >
    <div>

      <!-- <div
        :style="{ width: startWidth + 'px', height: startHeight + 'px', backgroundColor: backgroundColor, position: 'absolute', left: x + 'px', top: y + 'px' }"
        @mousedown="startResize"
        > -->
        <span :class="this.message ? 'message' : 'empty'">{{ this.message }}</span>
        <span class="height">{{ startHeight }}px</span>
        <span class="width">{{ startWidth }}px</span>
        <span style="margin:-30px 0 0 20px" >{{ startX }} - {{ startY }}</span>
      </div>
  </div>
</template>

<script>
export default {
  name: 'RectBloc',
    props: {
    x: {
      type: Number,
      default: 50
    },
    y: {
      type: Number,
      default: 100
    },
    width: {
      type: Number,
      default: 100
    },
    height: {
      type: Number,
      default: 100
    },
    backgroundColor: {
      type: String,
      default: 'red'
    },
    message: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      dragging: false,
      resizing: false,
      startX: this.x,
      startY: this.y,
      startWidth: this.width,
      startHeight: this.height,
      ecartX:0,
      ecartY:0,
      mouseX: 0,
      mouseY: 0,
      selected: false
    }
  },
  methods: {
    onClick(event) {
      let shape = event.target;
      shape.classList.toggle('selected');
        console.log('click', event.target)
    },
    startDragging(event) {
      if (event.target === this.$el) {
        this.dragging = true
        // position de la souris dans le canvas lors du drag

        // // position de la bordure gauche de l'élément dans le canvas
        // console.log(this.$el.offsetLeft)
        // // position de la souris par rapport au bord du canvas
        // console.log(event.clientX)
        // // position de la souris par rapport au bord gauche de l'élément
        // console.log(event.offsetX)
        // // position de la souris par rapport au bord du canvas
        // console.log(event.x)


        // je récupere la position de la souris sur le canvas
          this.mouseX = event.clientX;
          this.mouseY = event.clientY;

        // calcul de l'écart entre la position de la souris et la position des bords gauche et haut de l'élément
        this.ecartX = this.mouseX - this.$el.offsetLeft;
        this.ecartY = this.mouseY - this.$el.offsetTop;

        document.addEventListener('mousemove', this.drag)
        document.addEventListener('mouseup', this.stopDragging)
      }
    },
    drag(event) {
      if (this.dragging) {
        // je déplace l'élément en fonction de la position de la souris
        // position de la souris
        this.mouseX = event.x;
        this.mouseY = event.y;
        
        // nouvelle position de l'élément
        this.startX = this.mouseX - this.ecartX
        this.startY = this.mouseY - this.ecartY
      }
    },
    stopDragging() {
      if (this.dragging) {
        this.dragging = false
        document.removeEventListener('mousemove', this.drag)
        document.removeEventListener('mouseup', this.stopDragging)
      }
    },
    startResize(event) {
      if (event.target === this.$el) {
        this.resizing = true
        this.startX = event.clientX
        this.startY = event.clientY
        console.log(this.startX, this.startY);
        document.addEventListener('mousemove', this.resize)
        document.addEventListener('mouseup', this.stopResize)
      }
    },
    resize(event) {
      if (this.resizing) {
        const deltaX = event.clientX - this.startX
        const deltaY = event.clientY - this.startY
        this.startWidth += deltaX
        this.startHeight += deltaY
        this.startX = event.clientX
        this.startY = event.clientY
      }
    },
    stopResize() {
      if (this.resizing) {
        this.resizing = false
        document.removeEventListener('mousemove', this.resize)
        document.removeEventListener('mouseup', this.stopResize)
      }
    }
  }
}
</script>

<style>

    
    .rect {
        border: solid 1px black;
        cursor: move;
        user-select: none;
    }

    .rect:hover {
        background-color: #eee;
    }

    span {
        position: absolute;
        border-radius: 5px;
        padding: 0.5rem;
        font-size: 0.8rem;
        font-weight: 600;
    }

    .empty{
      display: none;
    }

    .message{
        background-color: #ffffff70;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    .height{
        background-color: #ffffff70;
        top: 25%;
        left: 0;
        transform: translateY(-50%);
    }

    .width{
        background-color: #ffffff70;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
    }

    .selected {
        box-shadow: inset 0 0 0 2px red;
    }

    div:hover {
        background-color: #eee;
    }

    div:active {
        background-color: #ddd;
    }

    div:active span {
        background-color: #ddd;
    }

    div:hover span {
        background-color: #eee;
    }

    div:active:hover {
        background-color: #ccc;
    }

    div:active:hover span {
        background-color: #ccc;
    }

</style>