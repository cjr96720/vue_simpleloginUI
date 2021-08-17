<template>
  <h1>Api Test</h1>
  <h1 :style="{ display: loginStatus ? '' : 'none' }">Hi, {{ memberName }}</h1>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      memberName: localStorage["memberName"],
    };
  },
  props: {
    loginStatus: Boolean,
  },
};
</script>

<style></style>
