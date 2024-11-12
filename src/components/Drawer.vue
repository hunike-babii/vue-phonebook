<template>
    <el-drawer
        :title="drawerType === 'add' ? '添加联系人' : '编辑联系人'"
        :model-value="drawerVisible"
        direction="btt"
        size="50%"
        @close="handleClose"
    >
        <el-form :model="form" label-width="120px" ref="formRef">
            <el-form-item 
                label="联系人姓名" 
                prop="name"
                :rules="[{ required: true, message: '请输入姓名', trigger: 'blur' }]"
            >
                <el-input v-model="form.name" />
            </el-form-item>
            <el-form-item 
                label="联系人电话" 
                prop="phone"
                :rules="[{ required: true, message: '请输入电话', trigger: 'blur' }]"
            >
                <el-input v-model="form.phone" />
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="handleSubmit">确定</el-button>
                <el-button @click="handleClose">取消</el-button>
            </el-form-item>
        </el-form>
    </el-drawer>
</template>

<script>
export default {
    props: {
        drawerVisible: Boolean,
        drawerType: String,
        // 添加编辑项的数据
        editData: {
            type: Object,
            default: () => ({})
        }
    },
    emits: ['close', 'submit'],
    data() {
        return {
            form: {
                name: '',
                phone: ''
            }
        }
    },
    watch: {
        // 监听编辑数据变化，更新表单
        editData: {
            handler(val) {
                if (this.drawerType === 'edit' && val) {
                    this.form = { ...val }
                }
            },
            immediate: true
        },
        // 监听抽屉关闭，重置表单
        drawerVisible(val) {
            if (!val) {
                this.resetForm()
            }
        }
    },
    methods: {
        handleClose() {
            this.$emit('close')
            this.resetForm()
        },
        handleSubmit() {
            this.$refs.formRef.validate((valid) => {
                if (valid) {
                    this.$emit('submit', { ...this.form })
                }
            })
        },
        resetForm() {
            if (this.$refs.formRef) {
                this.$refs.formRef.resetFields()
            }
            this.form = {
                name: '',
                phone: ''
            }
        }
    }
}
</script>

<style scoped>

</style>