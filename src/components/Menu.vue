<template>
    <el-menu
        class="el-menu-vertical-demo"
        :router="true">
        <el-menu-item v-for="(item, index) in menuList" :key="index" :index="item.path"
                :class="{ 'is-active': item.path === $route.path }">
            <i :class="item.icon"></i>
            <span slot="title">{{ item.title }}</span>
        </el-menu-item>
    </el-menu>
</template>

<script>

export default {
    name: 'Menu',
    props: {
        menuList: {
            type: Array,
            default: []
        }
    },
    methods: {
    }
}
</script>

<style>
</style>