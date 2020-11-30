<template>
  <div class="main">
    <form @submit.prevent="searchUser">
      <div class="searchBar-general">
        <input
          type="text"
          class="searchBar"
          name=""
          id=""
          v-model="username"
          placeholder="Digite o nickname do Github"
        />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  props: {
    method: { type: Function },
  },
  data() {
    return {
      username: "",
    };
  },
  methods: {
    searchUser() {
      this.method(this.username);
      this.username = "";
    },
  },
};
</script>

<style src="./style.css" scoped></style>
