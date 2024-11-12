<template>
  <div class="content">
    <List :list="list" @edit="editContact" @delete="deleteContact" />
    <el-button type="primary" round style="width: 100%; margin-top: 20px;" @click="addContact">添加</el-button>
    <Drawer 
      :drawerVisible="drawerVisible" 
      :drawerType="drawerType"
      :editData="currentEditItem"
      @close="closeDrawer" 
      @submit="handleSubmit" 
    />
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
        currentEditItem: null,
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
        this.currentEditItem = null
        this.drawerVisible = true
      },
      editContact(item) {
        this.drawerType = 'edit'
        this.currentEditItem = { ...item }
        this.drawerVisible = true
      },
      deleteContact(item) {
        this.$confirm('确认删除该联系人吗？', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.list = this.list.filter(i => i.id !== item.id)
          this.$message.success('删除成功')
        }).catch(() => {})
      },
      handleSubmit(form) {
        if (this.drawerType === 'add') {
          this.list.push({
            id: ++this.id,
            ...form
          })
        } else {
          const index = this.list.findIndex(i => i.id === this.currentEditItem.id)
          if (index > -1) {
            this.list[index] = {
              ...this.list[index],
              ...form
            }
          }
        }
        this.$message.success(this.drawerType === 'add' ? '添加成功' : '编辑成功')
        this.closeDrawer()
      },
      closeDrawer() {
        this.drawerVisible = false
        this.currentEditItem = null
      }
    }
  }
</script>

<style scoped>
  .content {
    padding: 20px;
  }
</style>
