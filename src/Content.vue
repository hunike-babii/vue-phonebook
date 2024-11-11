<template>
  <div class="content">
    <List :list="list" @edit="editContact" @delete="deleteContact" />
    <el-button type="primary" round style="width: 100%; margin-top: 20px;" @click="addContact">添加</el-button>
    <Drawer :drawerVisible="drawerVisible" :drawerType="drawerType" @close="closeDrawer" @submit="handleSubmit" />
  </div>
</template>

<script>
  import List from './components/List.vue'
  import Drawer from './components/Drawer.vue'
  export default {
    components: {
      List,
      Drawer
    },
    data() {
      return {
        drawerType: 'add',
        drawerVisible: false,
        id: 4,
        list: [
          {
            id: 1,
            name: '张三',
            phone: '1234567890'
          },
          {
            id: 2,
            name: '李四',
            phone: '1234567890'
          },
          {
            id: 3,
            name: '王五',
            phone: '1234567890'
          },
          {
            id: 4,
            name: '赵六',
            phone: '1234567890'
          }
        ]
      }
    },
    methods: {
      addContact() {
        this.drawerType = 'add'
        this.drawerVisible = true
      },
      closeDrawer() {
        this.drawerVisible = false
      },
      handleSubmit(form) {
        this.list.push({
          id: this.id++,
          ...form
        })
        this.drawerVisible = false
      },
      editContact(item) {
        this.$emit('edit',item)
        this.drawerType = 'edit'
        this.drawerVisible = true
      },
      deleteContact(item) {
        this.$emit('delete', item)
      }
    }
  }
</script>

<style scoped>
  .content {
    padding: 20px;
  }
</style>
