<template>
  <button :class="styleBtn" @click="$emit('click');" type="submit" >{{label}}</button>
</template>

<script>

export default {
  name: "AppButton",
  props: {
    label: {type: String},
  },

  /* computed: {
    styleBtn: function(){
      <style></style>
    }
  } */
}
</script>
