<template>
    <div class="layout">
        <Menu class="layout-header" mode="horizontal" theme="primary">
            <span class="layout-header-title">违法审核管理台</span>
            <right-menu/>
        </Menu>
        <left-menu/>
        <div class="layout-body">
            <router-view v-if="routerShow"/>
            <Spin size="large" fix v-else></Spin>
        </div>
    </div>
</template>

<script>
    import leftMenu from './left-menu';
    import rightMenu from './right-menu';
    import '../assets/style/layout.less';

    export default {
        data() {
            return {
                routerShow: false
            }
        },
        created() {
            this.$store.dispatch('getResources')
                .then(() => {
                    this.routerShow = true
                })
        },
        components: {leftMenu, rightMenu}
    }
</script>