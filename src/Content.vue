<template>
  <div>
    <List />
    <el-button type="primary" round style="width: 100%; margin-top: 20px;">添加</el-button>
    <Drawer />
  </div>
</template>

<script>
  import List from './components/List.vue'
  import Drawer from './components/Drawer.vue'
  export default {
    components: {
      List,
      Drawer
    }
  }
</script>

<style lang="scss" scoped>

</style>