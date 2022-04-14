<template>
  <input :placeholder="placeholderInput" :type="type"/>
</template>

<script>

export default {
  name: "AppInput",
  props: {
    placeholderInput: {type: String},
    type: {type: String}
  },

/*   data() {
    return {
      title: "placeholder",
    }
  } */
}
</script>
