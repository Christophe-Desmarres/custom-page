<template>
  <div>

    <rect 
      fill-opacity="0" 
      x="12" 
      y="64" 
      height="56" 
      width="149.40740585327148">
    </rect>

    

    <g 
      data-id="motion_movesteps" 
      class="blocklyDraggable" 
      data-shapes="stack" 
      data-category="motion"
      transform="translate(12,64)">

      <path 
        class="blocklyPath blocklyBlockBackground" 
        stroke="#3373CC" 
        fill="#4C97FF" 
        fill-opacity="1"
        d="m 0,4 A 4,4 0 0,1 4,0 H 12 c 2,0 3,1 4,2 l 4,4 c 1,1 2,2 4,2 h 12 c 2,0 3,-1 4,-2 l 4,-4 c 1,-1 2,-2 4,-2 H 145.40740585327148 a 4,4 0 0,1 4,4 v 40  a 4,4 0 0,1 -4,4 H 48   c -2,0 -3,1 -4,2 l -4,4 c -1,1 -2,2 -4,2 h -12 c -2,0 -3,-1 -4,-2 l -4,-4 c -1,-1 -2,-2 -4,-2 H 4 a 4,4 0 0,1 -4,-4 z">
      </path>

      <g 
        data-id="K_32Ypr;**[|E;4w{rBp" 
        data-argument-type="text number" 
        data-shapes="argument round"
        transform="translate(55.143516540527344,8)">
        <path 
          class="blocklyPath blocklyBlockBackground" 
          stroke="#3373CC" 
          fill="#FFFFFF" 
          fill-opacity="1"
          d="m 0,0 m 16,0 H 24 a 16 16 0 0 1 0 32 H 16 a 16 16 0 0 1 0 -32 z">
        </path>
        <g 
          class="blocklyEditableText" 
          transform="translate(8, 0) " 
          style="cursor: text;">
          <text 
            class="blocklyText" 
            x="12"
            y="18" 
            dominant-baseline="middle" 
            dy="0" 
            text-anchor="middle">
            10
          </text>
        </g>
      </g>
      <text 
        class="blocklyText" 
        y="2" 
        text-anchor="middle" 
        dominant-baseline="middle" 
        dy="0" 
        x="19.571758270263672"
        transform="translate(8, 24) ">
        move
      </text>
      <path 
        class="blocklyPath" 
        style="visibility: hidden" 
        d="" 
        fill="#3373CC">
      </path>
      <text class="blocklyText" y="2"
        text-anchor="middle" 
        dominant-baseline="middle" 
        dy="0" 
        x="19.13194465637207"
        transform="translate(103.14351654052734, 24) ">
        steps
      </text>
    </g>
  </div>
</template>

<script>
export default {
  name: 'CustomBlock',
  props: {
    msg: {
      type: String,
      required: true
    }
  }

}
</script>

<style></style>