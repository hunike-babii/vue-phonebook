<template>
    <el-drawer
        :title="drawerType === 'add' ? '添加联系人' : '编辑联系人'"
        :model-value="drawerVisible"
        direction="btt"
        size="50%"
        @close="$emit('close')"
    >
        <el-form :model="form" label-width="120px">
            <el-form-item label="联系人姓名">
                <el-input v-model="form.name" />
            </el-form-item>
            <el-form-item label="联系人电话">
                <el-input v-model="form.phone" />
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="handleSubmit">确定</el-button>
                <el-button type="danger" @click="$emit('close')">取消</el-button>
            </el-form-item>
        </el-form>
    </el-drawer>
</template>

<script>
export default {
    props: {
        drawerVisible: {
            type: Boolean,
            default: false
        }
    },
    data() {
        return {
            form: {
                name: '',
                phone: ''
            }
        }
    },
    methods: {
        handleSubmit() {
            this.$emit('submit', this.form)
        }
    }
}
</script>

<style scoped>

</style>