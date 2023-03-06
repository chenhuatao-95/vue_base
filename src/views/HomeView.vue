<template>
  <div class="home">
    <AboutView :msg="state.msg" @getMsg="getMsg"></AboutView>
  </div>
</template>

<script>
import { ref, reactive } from "vue";
import AboutView from "@/views/AboutView.vue";

export default {
  name: "HomeView",
  components: {
    AboutView,
  },
  setup() {
    var state = reactive({
      msg: 1,
    });
    function getMsg(val) {
      console.log(val, '子组件传来的值')
    }
    return {
      state,
      getMsg
    };
  },
};
</script>
