<template>
  <div class="test">
    <h1>{{ msg }}</h1>
    <p>the quick brown fox jumped over the lazy sheep dog !</p>
  </div>
</template>

<script>
export default {
  name: "AppTestComponent",
  props: {
    msg: String
  }
};
</script>