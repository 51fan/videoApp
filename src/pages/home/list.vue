<template>
  <ul class="swip_list" ref="listObj">
    <li
      v-for="item in listData"
      :key="item.id"
      v-items
      :class="{ active: item.active }"
      @click="showProjects(item)"
    >
      <el-button>{{ item.name }}</el-button>
    </li>
  </ul>
</template>
<script>
import eventBus from "@/utils/eventBus";
export default {
  data() {
    return {};
  },
  watch: {
    listData(newValue) {
      if (newValue) {
        this.showProjects(newValue[0]);
      }
    }
  },
  computed: {
    listData() {
      return this.$store.state.lisData;
    }
  },
  methods: {
    showProjects(obj) {
      this.listData.map(o => {
        o.active = false;
      });
      if (obj) {
        obj.active = true;
        eventBus.$emit("changeList", obj.length);
      }
    }
  }
};
</script>
<style scoped>
ul.swip_list {
  margin: 40px 50px;
}
ul.swip_list li {
  margin: 20px 0;
}
.el-button {
  width: 280px;
  height: 100px;
  font-size: 35px;
  font-weight: 600;
  color: #014bc0;
  font-family: 微软雅黑;
  background: rgba(255, 255, 255, 0.6);
  border-radius: 35px;
}
.el-button:hover,
ul.swip_list li.active button {
  background: url(../../static/image/home/menu_left_on.png) no-repeat 0 0;
  background-size: cover;
  color: yellow;
}
</style>
