<template>
  <header class="header">
    <h1>{{ titleHeader }}</h1>
    <div>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>



<script>
export default {
  name: "Header",
  data() {
    return {
      titleHeader: "APPLICATION TODO",
    };
  },
};
</script>


<style scoped>
.header {
  background: rebeccapurple;
  color: #fff;
  text-align: center;
  padding: 10px;
}

.header a {
  color: inherit;
  padding-right: 5px;
}
</style>
