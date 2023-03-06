<template>
  <div class="about">
    <h1>{{ state.message }}</h1>
    <button @click="changeMsg">点击</button>
    <button @click="test">点击+10</button>
  </div>
</template>
<script>
import { reactive, ref } from "vue";
export default {
  name: "AboutView",
  props: {
    msg: {
      type: Number,
    },
  },
  setup(props, context) {
    var state = reactive({
      message: props.msg,
      title: "about",
    });
    console.log(props, "父组件传来的值");
    function changeMsg() {
      context.emit("getMsg", state.title);
    }
    function test() {
      state.message += 10;
    }
    return {
      changeMsg,
      test,
      state,
    };
  },
};
</script>
