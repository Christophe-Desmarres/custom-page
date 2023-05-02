<template>
    <li class="drag-el list-group-item ">

        <div class="item_details">
        <i class="fa fa-align-justify handle"></i>
        {{dragelmt.name}}
        </div>
    </li>
</template>
<script>
export default {
    props: {
      dragelmt: Object,
      default: () => ({})
    },
 }
</script>
  