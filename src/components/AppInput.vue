<template>
  <div class="boxInput">
    <label for="time">{{ label }}</label>
    <input :type="type" />
  </div>
</template>

<script>
export default {
  name: "AppInput",
  props: {
    label: { type: String },
    type: { type: String },
  },
};
</script>

<style>
  label {
    justify-content: left;
    display: flex;
    font-size: 12px;
    margin-bottom: 8px;
    color: #707070;
  }

  input {
    padding: 8px;
    /* border: 1px solid #FF4200; */
    border-radius: 8px;
    border: none;
    height: 20px;
    width: 200px;
    background-color: white;
  }
</style>
