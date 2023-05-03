<template>
                        <svg height="140" width="auto">
                        <ellipse cx="50%" cy="70" rx="20%" ry="20%"
                        style="fill:yellow;stroke:purple;stroke-width:2" />
                      <text 
                      y="50%" 
                      x="35%"
                      >
                      - {{ dragelmt.name }}
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
  