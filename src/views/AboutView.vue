<template>
  <div class="about">
    <h1>{{ state.message }}</h1>
    <button @click="changeMsg">点击</button>
    <button @click="test">点击+10</button>
  </div>
</template>
<script>
import { reactive, ref, watch } from "vue";
export default {
  name: "AboutView",
  props: {
    msg: {
      type: Number,
    },
  },
  setup(props, context) {
    var state = ref({
      message: props.msg,
      title: "about",
    });
    console.log(props, "父组件传来的值");
    function changeMsg() {
      context.emit("getMsg", state.title);
    }
    function test() {
      state.value.message += 10;
    }
    watch(state.value,(newValue,oldValue) => {
      console.log(newValue,oldValue)
    })
    return {
      changeMsg,
      test,
      state,
    };
  },
};
</script>
