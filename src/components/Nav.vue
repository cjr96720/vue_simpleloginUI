<template>
  <div class="navbar">
    <ul class="menu-bar">
      <router-link to="/"><li>Home</li></router-link>

      <router-link to="/login" :style="{ display: loginStatus ? 'none' : '' }"
        ><li>Login</li></router-link
      >
      <router-link to="/" :style="{ display: loginStatus ? '' : 'none' }"
        ><li>{{ memberName }}</li></router-link
      >
      <router-link
        @click="$emit('logout-click')"
        to="/"
        :style="{ display: loginStatus ? '' : 'none' }"
        ><li>Logout</li></router-link
      >
    </ul>
  </div>
</template>

<script>
export default {
  name: "Nav",
  data() {
    return {
      memberName: localStorage["memberName"],
    };
  },
  props: {
    loginStatus: Boolean,
    memberInfo: Object,
  },
};
</script>

<style scoped>
.navbar {
  text-align: center;
}

.menu-bar {
  border-radius: 25px;
  height: fit-content;
  display: inline-flex;
  background-color: rgba(0, 0, 0, 0.4);
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
  align-items: center;
  padding: 0 10px;
  margin: 50px 0 0 0;
}
.menu-bar li {
  list-style: none;
  color: white;
  font-family: sans-serif;
  font-weight: bold;
  padding: 12px 16px;
  margin: 0 8px;
  position: relative;
  cursor: pointer;
  white-space: nowrap;
}
.menu-bar li::before {
  content: " ";
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  z-index: -1;
  transition: 0.2s;
  border-radius: 25px;
}
.menu-bar li:hover {
  color: black;
}
.menu-bar li:hover::before {
  background: linear-gradient(to bottom, #e8edec, #d2d1d3);
  box-shadow: 0px 3px 20px 0px black;
  transform: scale(1.2);
}

a:link {
  text-decoration: none;
}

.badge {
  display: inline-block;
  padding: 0.25em 0.4em;
  font-size: 90%;
  font-weight: 700;
  line-height: 1;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: 0.25rem;
}
</style>
