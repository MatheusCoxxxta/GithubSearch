<template>
  <div class="general">
    <div class="main" v-if="data">
      <ul v-for="repos in data" :key="repos.name">
        <li class="reposList" @click="redirect(repos.owner.login, repos.name)">
          <label class="name" for="">
            {{ repos.name.slice(0, 30) }}
            {{ repos.name.length > 30 ? "..." : "" }}
          </label>
          <label class="owner" for="">
            {{ repos.owner.login }}
          </label>
        </li>
      </ul>
    </div>
    <div v-else>Nenhum usuário foi buscado até o momento...</div>
    <div v-if="errorMsg">{{ errorMsg }}</div>
  </div>
</template>

<script>
export default {
  name: "RepoList",
  props: ["data", "errorMsg"],
  methods: {
    redirect(username, repo) {
      window.open(`https://www.github.com/${username}/${repo}`, "_blank");
    },
  },
  mounted() {
    this.data = "";
  },
};
</script>

<style src="./style.css" scoped></style>
