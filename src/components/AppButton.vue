<template>
  <button :type="type" >{{label}}</button>
</template>

<script>

export default {
  name: "AppButton",
  props: {
    label: {type: String},
    type: { type: String },
  },
}
</script>

<style>
  button {
    padding: 8px;
    /* border: 1px solid #ffffff; */
    border: none;
    border-radius: 50px;
    background-color: #1e2626;
    color:white;
    height: 40px;
    width: 120px;
    margin-top: 24px;
    cursor: pointer;
  }
</style>