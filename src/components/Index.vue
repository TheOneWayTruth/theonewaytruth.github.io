<template>
  <div>
    <h1 class="caption">Projects</h1>
    <div>
      <span class="text">
        You like my projects? why dont you
        <span class="link">
          <a href="https://www.buymeacoffee.com/a4bl2n1">buy me a Coffe</a>
        </span>?
      </span>
    </div>
    <div class="flex">
      <div class="kiste" :key="item.id" v-for="item in projects">
        <div class="title">{{item.name}}</div>
        <span>{{item.desc}}</span>
        <div
          :class="{disabled:site.disabled}"
          class="link"
          :key="site.id"
          v-for="site in item.sites"
        >
          <a :href="getlink(site)">{{site.name}}</a>
        </div>
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
    }
  },
  data() {
    return {
      projects: projectlist
    };
  }
};
</script>

<style scoped>
.flex {
  display: flex;
  flex-wrap: wrap;
}
.kiste {
  margin: 10px;
  padding: 15px;
  border: 1px solid white;
  box-shadow: 5px 10px green inset;
}

.title {
  margin: 0px 0px 10px 0px;
  font-size: 25px;
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