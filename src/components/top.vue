<template>
    <div id="top">
        <img src="../assets/imgs/logo.jpg" class="pic" />
        <ul class="listTop">
            <li v-for="(item, index) in list" :key="index">{{ item }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    inject: ['ListTop'],
    data() {
        return {
            list: this.ListTop,
        }
    },
}
</script>

<style lang="scss" scoped>
@import '../assets/sass/top.scss';
</style>