<template>
    <div class="list-container">
        <!-- 使用 v-for 遍历列表数据 -->
        <el-card 
            v-for="item in list" 
            :key="item.id" 
            class="list-item"
            shadow="always"
        >
            <div class="list-content">
                <div class="list-info">
                    <span class="name">{{ item.name }}</span>
                    <span class="phone">{{ item.phone }}</span>
                </div>
                <div class="list-actions">
                    <el-button type="success" circle size="small">
                        <el-icon :size="17"><PhoneFilled si/></el-icon>
                    </el-button>
                    <el-button type="primary" circle size="small" @click="$emit('edit', item)">
                        <el-icon :size="17"><Edit /></el-icon>
                    </el-button>
                    <el-button type="danger" circle size="small" @click="$emit('delete', item)">
                        <el-icon :size="17"><DeleteFilled /></el-icon>
                    </el-button>
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
    emits: ['edit', 'delete']
}
</script>

<style scoped>
.list-container {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.list-item {
    margin-bottom: 0;
}

.list-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.list-info {
    display: flex;
    gap: 20px;
    font-size: 16px;
}

.list-actions {
    display: flex;
    gap: 8px;
}

.name {
    font-weight: bold;
}

.phone {
    color: #666;
}
</style>