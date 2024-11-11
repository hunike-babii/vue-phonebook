<template>
    <div class="drawer">
        <el-drawer v-model="drawerVisible" direction="btt" show-close="false" title="添加联系人" size="50%">
            <el-form :model="form" label-width="120px">
                <el-form-item label="联系人姓名">
                    <el-input />
                </el-form-item>
                <el-form-item label="联系人电话">
                    <el-input />
                </el-form-item>
                <el-form-item>
                    <el-button type="primary">确定</el-button>
                    <el-button type="danger">取消</el-button>
                </el-form-item>
            </el-form>
        </el-drawer>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                drawerVisible: true,
                form: {
                    name: '',
                    phone: ''
                }
            }
        }
    }
</script>

<style scoped>

</style>