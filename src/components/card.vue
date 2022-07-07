<template>
  <div class="card">
    <a :href="anime.url">
      <div class="img">
        <img
          :src="anime.image_url"
          alt=""
        />
      </div>
      <div class="name">
        <h1>{{anime.title}}</h1>
      </div>
    </a>
  </div>
</template>

<script>
export default {
    setup() {
        
    },
    props:['anime']
}
</script>

<style>
a {
  color: white;
  text-decoration: none;
}
.card {
  color: white;
  width: 225px;
  height: 317px;
  position: relative;
  margin: 20px 20px;
}
.card .name{
    position: absolute;
    bottom: 0px;
    background-color: rgba(0, 0, 0, 0.57);
    width: 225px;
    font-size: 10px;
    height: 60px;
    text-align: center;
}
</style>
