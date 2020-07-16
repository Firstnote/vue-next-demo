<template>
  <div>
    <h2>{{title}}</h2>
    <h2>{{$attrs.userName}}</h2>
    <child v-bind="$props"></child>
    <div v-for="(item,index) in arr" :key="item" @click="change(index,arr)">{{item}}</div>
    <div v-for="(item,index) in state.arr" :key="item" @click="change(index,state.arr)">{{item}}</div>
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
  reactive,
  toRefs
} from "vue";
import child from "./child";
export default {
  components: {
    child
  },
  props: {
    userName: {
      type: String
    }
    // url: {
    //   required: false
    // }
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
    const change = (index, arr) => {
      // console.log(index);
      // state.arr[index] = 20;
      // state.arr.splice
      // state.arr[index]++;
      arr[index].name = arr[index].name === "xiaohui" ? "xiaoqiao" : "xiaohui";
    };
    onMounted(() => {
      title.value = "sss";
      console.log("props", props);
    });
    onBeforeMount(() => {
      console.log("context", context.attrs.url);
    });
    onMounted(() => {});

    return {
      title,
      state,
      change,
      ...toRefs(state) //属性指针不变
    };
  }
};
</script>
