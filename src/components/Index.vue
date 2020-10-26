<template>
  <div>
    <h1 class="caption">Projects</h1>
    <div>
      <span class="text">
        You like my projects? why dont you
        <span class="link">
          <a href="https://www.paypal.me/wickalexander/2"
            >buy me a Coffe</a
          > </span
        >?
      </span>
    </div>
    <div class="flex">
      <div class="kiste" :key="item.id" v-for="item in projects">
        <img class="icon" :src="getImgIcon(item.id)" alt="image" />
        <div class="title">{{ item.name }}</div>

        <div>{{ item.desc }}</div>
        <img class="img" :src="getImgUrl(item.id)" alt="image" />
        <div
          :class="{ disabled: site.disabled }"
          class="link"
          :key="site.id"
          v-for="site in item.sites"
        >
          <a :href="getlink(site)">{{ site.name }}</a>
        </div>
        <br />
        <div>Todo:</div>
        <div>{{ item.task }}</div>
        <br />
        <div class="status">status: {{ item.status }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import projectlist from "./Projects.json";

export default {
  name: "index",
  methods: {
    getlink(i) {
      if (i.disabled) {
        return;
      }
      return i.link;
    },
    getImgUrl(val) {
      var images = require.context("../assets/img/", false, /\.png$/);
      return images("./" + val + ".png");
    },
    getImgIcon(val) {
      var images = require.context("../assets/icons/", false, /\.png$/);
      return images("./" + val + ".png");
    },
  },
  data() {
    return {
      projects: projectlist,
    };
  },
};
</script>

<style scoped>
.icon {
  float: left;
  width: 32px;
  margin-right: 10px;
}
.img {
  width: 300px;
  height: 150px;
  margin: 4px;
  border: 1px solid green;
  object-fit: cover;
}
.status {
  color: yellow;
  position: absolute;
  right: 10px;
  bottom: 10px;
}
.flex {
  display: flex;
  flex-wrap: wrap;
}
.kiste {
  position: relative;
  min-width: 300px;
  margin: 10px;
  padding: 15px;

  box-shadow: 5px -5px green inset;
  background: #303030;
}

.title {
  margin: 0px 0px 10px 0px;
  font-size: 25px;
  line-height: 32px;
}
.link > a {
  cursor: crosshair;
  text-decoration: none;
  color: green;
  margin-top: 10px;
  line-height: 10px;
}
.link > ::before {
  content: "> ";
}
.link > :hover {
  font-family: Impact, Haettenschweiler, "Arial Narrow Bold", sans-serif;
}
.disabled > a {
  color: grey;
}
.text {
  margin-left: 10px;
}
.caption {
  margin: 20px;
  font-size: 100px;
}
</style>