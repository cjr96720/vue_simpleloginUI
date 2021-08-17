<template>
  <div>
    <Nav :loginStatus="loginStatus" @logout-click="logout" />
    <router-view @toggle-status="toggleStatus" :loginStatus="loginStatus">
    </router-view>
  </div>
</template>

<script>
import Nav from "./components/Nav";
export default {
  name: "App",
  components: {
    Nav,
  },
  data() {
    return {
      loginStatus: false,
      memberInfo: {
        memberid: 0,
        memberName: "",
        memberEmail: "",
      },
    };
  },
  methods: {
    toggleStatus(info) {
      console.log(info);
      this.memberInfo.memberName = info["membername"];
      console.log(this.memberInfo.memberName);

      localStorage.setItem("memberName", this.memberInfo.memberName);

      this.loginStatus = !this.loginStatus;

      this.$router.push("/");
    },
    logout() {
      this.loginStatus = !this.loginStatus;

      this.memberInfo.memberid = 0;
      this.memberInfo.memberName = "";
      this.memberInfo.memberEmail = "";

      localStorage.clear();

      this.$router.push('/');
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  padding: 0;
  margin: 0;
}

body {
  font-family: "Poppins", sans-serif;
}

h1 {
  text-align: center;
  margin: 20px auto;
}
</style>
