<template>
  <div>
    <search-bar data="MatheusCoxxxta" :method="handleSearch" />
    <repo-list :data="reposArray" :errorMsg="errMsg" />
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar/";
import RepoList from "./components/RepoList/";
import { githubAPI } from "../../services/githubAPI";

export default {
  name: "Main",
  components: {
    SearchBar,
    RepoList,
  },
  data() {
    return {
      reposArray: [],
      errMsg: "",
    };
  },

  methods: {
    handleSearch: async function(username) {
      console.log("Github Username: ", username);

      githubAPI
        .get(`${username}/repos`)
        .then(async (response) => {
          this.reposArray = await response.data;
        })
        .catch(() => {
          this.reposArray = [];
          this.errMsg = "Nenhum usuário foi encontrado...";
        });
    },
  },
};
</script>

<style>
body {
  background-color: #eeeeee;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
}
</style>
