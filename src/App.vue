<template>
  <div class="title">Tìm kiếm Anime</div>
  <div class="search">
    <form action="">
      <input
        type="search"
        class="search-box"
        v-model="search_query"
        @change="HandleSearch"
      />
      <i class="fa-solid fa-magnifying-glass search-icon"></i>
    </form>
  </div>

  <div class="list_result">
    <card  v-for="anime in search_result" :anime="anime" />
  </div>
</template>
<script>
import { ref } from "vue";
// import axios from "axios";
import card from "./components/card.vue";
export default {
  setup() {
    const search_query = ref("");
    const search_result = ref([]);
    const api_anime = `https://api.jikan.moe/v3/search/anime?q=`;
    const HandleSearch = async () => {
     search_result.value = await fetch(api_anime + search_query.value)
				.then(res => res.json())
				.then(data => data.results);

        console.log(search_result.value);
    };
    return {
      search_query,
      api_anime,
      search_result,
      HandleSearch,
    };
  },
  methods: {},
  components: { card },
};
</script>

<style lang="css">
body {
  background-color: #2a2e37;
  font-family: sans-serif;
}

.title {
  text-align: center;
  color: #00fede;
  font-size: 40px;
  margin: 100px 0px 50px 0px;
}
.search {
  width: 400px;
  margin: auto;
  position: relative;
}
.search-box {
  width: 400px;
  padding: 20px;
  font-size: 25px;
  background-color: #242628;
  border: none;
  outline: none;
  color: white;
}
.search-icon {
  color: #00fede;
  font-size: 30px;
  position: absolute;
  right: 5%;
  top: 30%;
}

.list_result {
  display: flex;
  flex-wrap: wrap;
  margin: 70px;
}

[type="search"]::-webkit-search-cancel-button,
[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
  appearance: none;
}
</style>
