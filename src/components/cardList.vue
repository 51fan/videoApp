<template>
  <div>
    <div class="header">
      <span class="line">——</span>
      <span class="title">{{ project.name }}</span>
      <span class="line">——</span>
    </div>
    <div
      class="videoPro"
      @click="openDetails"
      v-for="item in project.list"
      :key="item.id"
      v-items
    >
      <el-card>
        <img :src="item.img" class="image" />
      </el-card>
    </div>
  </div>
</template>
<script>
export default {
  props: ["project"],
  data() {
    return {};
  },
  methods: {
    openDetails() {
      this.$router.push({ path: "/details" });
    }
  }
};
</script>
<style>
.videoPro {
  cursor: pointer;
  width: 25%;
  float: left;
  margin: 0 4%;
}
.header {
  font-size: 30px;
  margin-bottom: 30px;
}
.header .title {
  font-weight: 600;
}
.card_bottom {
  height: 50px;
  line-height: 50px;
  background: rgba(0, 0, 0, 0.6);
  position: absolute;
  bottom: 0px;
  width: 100%;
  left: 0;
}

.videoPro .button {
  padding: 0;
  color: #fff;
  font-size: 20px;
}

.videoPro .image {
  width: 100%;
  display: block;
}

.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}

.clearfix:after {
  clear: both;
}
.videoPro .el-card__body {
  padding: 0px !important;
}
.videoPro .el-card {
  border: 2px solid #000 !important;
  border-radius: 20px !important;
  height: 100%;
  position: relative;
}
.videoPro .el-card:hover {
  border: 2px solid yellow !important;
  box-shadow: 0px 2px 30px yellow !important;
}
</style>
