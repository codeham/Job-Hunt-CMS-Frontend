<template>
  <div class="test">
    <H1>This is the Data Binding Component !</H1>
    <div>
      <div v-for="user in users" :key="user.username">
        <p>Username: {{ user.username }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBindingComponent",
  data: function() {
    return {
      users: [
        { username: "Max" },
        { username: "Cristian" },
        { username: "Fred" },
      ],
    };
  },
  props: {
    msg: String,
  },
};
</script>
