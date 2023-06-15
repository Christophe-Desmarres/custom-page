<script setup>
defineProps({
  list: {
    name: Object,
    required: true
  },
  listName: {
    type: String,
    required: true
  },
});
</script>

<template>
        <div class="selection">
          <select class="choose__select" :v-model="list">
          <option disabled value="" selected>Choose your {{ listName }}</option>
          <option v-for="object in list" :key="object.id" :value="object.id">
            {{ object.name }}
          </option>
        </select>
        <div id="chevrons">
          <i class="fas fa-chevron-up"></i>
          <i class="fas fa-chevron-down"></i>
      </div>
      </div>
</template>


<style >

/* ----------------- */
/* selection element */
/* ----------------- */

*:focus {
  outline: none;
}

select{
  appearance: none;
  width: 100%;
  height: 100%;
  border: none;
  background-color: transparent;
  font-size: 1.25rem;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}



.choose__select {
  display: block;
  margin: 1rem 0 1rem 1rem;
  border-radius: 0.25em;
  padding: 0.25em 0.5em;
  cursor: pointer;
  line-height: 1.1;
  background-color: #fff;
  background-image: linear-gradient(to top, #f9f9f9, #fff 33%);
}

.selection{
  position: relative;
  width: 40%;
}

#chevrons {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  width: 12px;
  padding: 9px;
}

#chevrons i {
  display: block;
  height: 50%;
  color: #d1dede;
  font-size: 0.8rem;
}


@media screen and (max-width: 768px) {
  .selection{
    width: 70%;
    margin: auto;
  }
  .choose__select{
    font-size: 1.25rem;
    line-height: 2;
  }
}

@media screen and (max-width: 480px) {
  select{
  }
  .selection{
    width: 100%;
    margin: auto;
  }
  .choose__select{
    font-size: 1rem;
    line-height: 2;
    margin: 1rem 0 1rem 0;
  }
}

</style>