<template>
  <div>
    <input type="text" @change="change" />
    <div>{{msg1}}</div>
    <div>{{msg2}}</div>
  </div>
</template>
<script>
import { onMounted, reactive, toRefs, computed, watch } from "vue";
export default {
  name: "child",
  setup(props, context) {
    onMounted(() => {
      console.log("child", context.attrs);
    });

    // computed test
    const state = reactive({
      txt: ""
    });
    const msg1 = computed(() => {
      return `msg1:${state.txt}`;
    });
    const msg2 = computed({
      get() {
        return `msg2:${state.txt}`;
      },
      set(val) {
        state.txt = val;
      }
    });
    const change = e => {
      console.log(e.target.value);
      msg2.value = e.target.value;
    };

    // watch test

    return {
      ...toRefs(state),
      change,
      msg1,
      msg2
    };
  }
};
</script>