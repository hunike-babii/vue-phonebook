<template>
    <div class="list">
        <el-card>
            <div class="list-header">
                <div class="list-information">
                    <span>姓名</span>
                    <span>电话号码</span>
                </div>
                <div class="list-operate">
                    <el-icon :size="25" color="green"><PhoneFilled /></el-icon>
                    <el-icon :size="25" color="blue"><Edit /></el-icon>
                    <el-icon :size="25" color="red"><DeleteFilled /></el-icon>
                </div>
            </div>
        </el-card>
    </div>
</template>

<script>
    export default {
        
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
</style>