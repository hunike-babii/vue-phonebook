<template>
    <div class="list" v-for="item in list" :key="item.id">
        <el-card>
            <div class="list-header" >
                <div class="list-information">
                    <span>{{ item.name }}</span>
                    <span>{{ item.phone }}</span>
                </div>
                <div class="list-operate">
                    <el-icon :size="25" color="green"><PhoneFilled /></el-icon>
                    <el-icon :size="25" color="blue"><Edit @click="editContact(item)" /></el-icon>
                    <el-icon :size="25" color="red"><DeleteFilled @click="deleteContact(item)" /></el-icon>
                </div>
            </div>
        </el-card>
    </div>
</template>

<script>
    export default {
        props: {
            list: {
                type: Array,
                required: true
            }
        },
        emits: ['edit', 'delete'],
        methods: {
            editContact(item) {
                this.$emit('edit', item)
            },
            deleteContact(item) {
                this.$emit('delete', item)
            }
        }
    }
</script>

<style scoped>
    .list-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .list-operate {
        display: flex;
        gap: 10px;
    }
    .list {
        margin-bottom: 10px;
    }
</style>