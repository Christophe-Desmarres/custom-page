<template>
  <div       
    class="rect"
    :style="{ width: startWidth + 'px', height: startHeight + 'px', backgroundColor: backgroundColor, position: 'absolute', left: startX + 'px', top: startTop + 'px', cursor: dragging ? 'move' : 'default' }"
    @mousedown="startDragging"
    >
      <!-- <div
        :style="{ width: startWidth + 'px', height: startHeight + 'px', backgroundColor: backgroundColor, position: 'absolute', left: x + 'px', top: y + 'px' }"
        @mousedown="startResize"
        > -->
        <span id="height">{{ startHeight }}px</span>
        <span id="width">{{ startWidth }}px</span>
  </div>
</template>

<script>
export default {

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
    }
  },
  data() {
    return {
      dragging: false,
      resizing: false,
      startX: 0,
      startY: 0,
      startWidth: this.width,
      startHeight: this.height,
      startLeft: 0,
      startTop: 0
    }
  },
  methods: {
    startDragging(event) {
      if (event.target === this.$el) {
        this.dragging = true
        this.startX = event.clientX
        this.startY = event.clientY
        this.startLeft = this.x
        this.startTop = this.y
        console.log(this.startX, this.startY);
        console.log(this.startLeft, this.startTop);
        document.addEventListener('mousemove', this.drag)
        document.addEventListener('mouseup', this.stopDragging)
      }
    },
    drag(event) {
      if (this.dragging) {
        const deltaX = event.clientX - this.startX
        const deltaY = event.clientY - this.startY
        this.startX = this.startLeft + deltaX
        this.starty = this.startTop + deltaY
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
    }

    .rect:hover {
        background-color: #eee;
        box-shadow: inset 0 0 0 5px #000;
    }

    span {
        position: absolute;
        background-color: white;
        padding: 0.5rem;
        font-size: 0.8rem;
    }

    #height{
        top: 50%;
        left: 0;
        transform: translateY(-50%);
    }

    #width{
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
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