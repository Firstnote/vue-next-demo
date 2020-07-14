<template>
  <div>
    <h2>{{title}}</h2>
    <h2>{{userName}}</h2>
    <div v-for="(item,index) in state.arr" :key="item" @click="change(index)">{{item}}</div>
  </div>
</template>

<script>
import {
  onBeforeMount,
  onMounted,
  // onBeforeUpdate,
  // onUpdated,
  // onBeforeUnmount,
  // onUnmounted,
  // onErrorCaptured,
  // onRenderTracked,
  // onRenderTriggered,
  ref,
  reactive
} from "vue";

export default {
  props: {
    userName: {
      type: String
    }
  },
  setup(props, context) {
    const title = ref("demo");
    // 数组系列
    const state = reactive({
      arr: [
        {
          name: "xiaoqiao"
        },
        {
          name: "xiaoqiao"
        },
        {
          name: "xiaoqiao"
        },
        {
          name: "xiaoqiao"
        }
      ]
    });
    const change = index => {
      // console.log(index);
      // state.arr[index] = 20;
      // state.arr.splice
      // state.arr[index]++;
      state.arr[index].name =
        state.arr[index].name === "xiaohui" ? "xiaoqiao" : "xiaohui";
    };
    onMounted(() => {
      title.value = "sss";
      console.log("props", props);
    });
    onBeforeMount(() => {
      console.log("context", context);
    });
    onMounted(() => {});

    return {
      title,
      state,
      change
    };
  }
};
</script>
