<template>
  <div>
    <headerBlock></headerBlock>

    <div class="bannerBlog">
      <img src="../assets/projectDetails/banner.svg" alt="banner" />
    </div>

    <div class="projectDetails center">
      <p class="projectDetails__title"> {{ selectedProject.title }}</p>
      <p class="projectDetails__desc"> {{ selectedProject.description }}</p>
      <img class="projectDetails__img" :src="selectedProject.img[0].path" :alt="selectedProject.img[0].path">
    </div>

    <footerBlock />
  </div>
</template>

<script>
import headerBlock from "./universal/header.vue";
import footerBlock from "./universal/footer.vue";
import store from "@/store/index";

export default {
  name: "ProjectDetails",
  components: {
    headerBlock,
    footerBlock
  },
  props: {},
  data() {
    const selectedProjectId = 1;
    return {
      selectedProjectId
    };
  },
  computed: {
    selectedProject() {
      return store.state.projectsList.filter(p => p.id === this.selectedProjectId)[0];
    },
  },
  methods: {
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  color: rgba(41, 47, 54, 1);
}
.center {
  padding-left: calc(50% - 600px);
  padding-right: calc(50% - 600px);
}
</style>

<style scoped>
.bannerBlog {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 44px;
  position: relative;
  font-family: "Jost";
  overflow: hidden;
}

.projectDetails {
  margin-top: 200px;
}

.projectDetails__title {
  font-family: "DM Serif Display";
  font-size: 50px;
  padding-left: 271px;
  padding-right: 271px;
}

.projectDetails__desc {
  margin-top: 10px;
  font-family: "Jost";
  font-size: 22px;
  padding-left: 271px;
  padding-right: 271px;
}

.projectDetails__img {
  margin-top: 100px;
  border-radius: 60px;
}
</style>
