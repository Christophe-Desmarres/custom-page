<template>
  <div  
    :id="'diamond' + this.id"     
    class="diamond"
    :style="{ width: startWidth + 'px', height: startHeight + 'px', backgroundColor: backgroundColor, position: 'absolute', left: startX + 'px', top: startY + 'px', cursor: dragging ? 'move' : 'default' }"
    @mousedown="startDragging"
    >
    <div>

      <!-- <div
        :style="{ width: startWidth + 'px', height: startHeight + 'px', backgroundColor: backgroundColor, position: 'absolute', left: x + 'px', top: y + 'px' }"
        @mousedown="startResize"
        > -->
        <span contenteditable="true" :class="this.message ? 'message' : 'empty'">{{ this.message }}</span>
        <span class="height">{{ startHeight }}px</span>
        <span class="width">{{ startWidth }}px</span>
        <span style="margin:-30px 0 0 20px" >{{ startX }} - {{ startY }}</span>
      </div>
  </div>
</template>

<script>
export default {
  name: 'DiamondBloc',
    props: {
    id: {
      type: Number      
    },
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
      selected: ""
    }
  },
  methods: {
    onClick(event) {

      // je récupère l'élément selectionné
      this.selected = event.target;

      // je déselectionne tout les autres éléments
      let allSelected = document.querySelectorAll('.selected');
      allSelected.forEach((element) => {
        element.classList.remove('selected');
      });

      // j'ajoute la class selected à l'élément selectionné
      this.selected.classList.add('selected');

    },
    startDragging(event) {
      if (event.target === this.$el) {
        this.dragging = true
        this.onClick(event);

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

    
    .diamond {
        border: solid 1px black;
        transform: rotate(45deg);
        cursor: move;
        user-select: none;
    }

    .diamond:hover {
        background-color: #eee;
    }

    .diamond span {
        position: absolute;
        border-radius: 5px;
        padding: 0.5rem;
        font-size: 0.8rem;
        font-weight: 600;
        transform: rotate(-45deg);

    }

    .diamond .empty{
      display: none;
    }

    .diamond .message{
        background-color: #ffffff70;
        top: 30%;
        left: 30%;
        transform: translate(-50%, -50%);
        transform: rotate(-45deg);

    }

    .diamond .height{
        background-color: #ffffff70;
        top: 25%;
        left: 0;
        transform: translateY(-50%);
        transform: rotate(-45deg);

    }

    .diamond .width{
        background-color: #ffffff70;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
        transform: rotate(-45deg);

    }

    .selected {
        box-shadow: inset 0 0 0 2px red;
    }


    .diamond:active span {
        background-color: #ddd;
    }

    .diamond:hover span {
        background-color: #eee;
    }

    .diamond:active:hover {
        background-color: #ccc;
    }

    .diamond:active:hover span {
        background-color: #ccc;
    }

</style>