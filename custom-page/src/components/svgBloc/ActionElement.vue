<template>
                
                <svg height="30" width="auto">
                    <rect x="0" y="0" rx="5" ry="5" width="100%" height="100%" style="fill:red;stroke:black;stroke-width:5;opacity:0.5" />
                    Sorry, your browser does not support inline SVG.
               
                      <text 
                      y="20" 
                      x="5"
                      >
                      {{ dragelmt.name }}
                    </text>

                  </svg>
</template>
<script>
export default {
    props: {
      dragelmt: Object,
      default: () => ({})
    },
 }
</script>
  