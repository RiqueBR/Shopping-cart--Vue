<template>
  <transition
    name="custom"
    enter-active-class="animated fadeInDown"
    leave-active-class="animated slideOutRight"
  >
    <div v-if="sliderStatus">
      <div class="align-items-center" :class="sliderState">
        <label :class="labelArr" for="formMax">max</label>
        <input
          type="text"
          id="formMax"
          class="form-control mx-2"
          :style="{'width': inputWidth + 'px', textAlign:'center'}"
          v-model="maximum"
        >
        <input type="range" class="custom-range" min="0" max="200" v-model="maximum">
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "price-slider",
  props: ["sliderStatus"],
  computed: {
    sliderState: function() {
      return this.sliderStatus ? "d-flex" : "d-none";
    }
  }
};
</script>


<style>
</style>
