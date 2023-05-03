<template>
                    <svg height="30" width="auto">
                      <text 
                      y="20" 
                      x="10"
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
  