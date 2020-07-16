<template>
  <div></div>
</template>
<script>
import { onMounted } from "vue";
export default {
  name: "child",
  setup(props, context) {
    onMounted(() => {
      console.log("child", context.attrs);
    });
  }
};
</script>