<template>
  <div class="about">
    <h1>{{ state.message }}</h1>
    <el-button type="primary" @click="changeMsg">点击</el-button>
    <el-button type="danger" @click="test">点击 + 10</el-button>
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
    watch(state,(newValue,oldValue) => {
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
