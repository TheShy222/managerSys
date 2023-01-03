<script>
import top from './components/top.vue'
import update from './components/update.vue'
import { computed } from 'vue'
export default {
    components: {
        update,
        top,
    },
    data() {
        return {
            accountName: '',
            name: '',
            sex: '',
            password: '',
            show: false,
            listTop: ['切换账号', '消息', '退出'],
            listLeft: [
                '我的任务',
                '项目管理',
                '问题管理',
                '任务评价',
                '档案库',
                '组织管理',
                '用户管理',
            ],
        }
    },
    provide() {
        return {
            ListTop: computed(() => this.listTop),
        }
    },
    methods: {
        updateInfo() {
            this.show = false
        },
    },
}
</script>

<template>
    <top :listTop="listTop"></top>
    <div id="bottom">
        <div class="left">
            <ul class="listLeft">
                <li v-for="(item, index) in listLeft" :key="index">
                    {{ item }}
                </li>
            </ul>
        </div>
        <div class="right">
            <div class="info">
                <div class="top">
                    <h2>个人信息</h2>
                    <button @click="show = true">修改</button>
                </div>
                <div class="bot">
                    账号名:<input type="text" v-model="accountName" />
                    <br />
                    姓&emsp;名:<input type="text" v-model="name" /><br />
                    性&emsp;别:<input type="text" v-model="sex" /><br />
                    密&emsp;码:<input type="text" v-model="password" />
                </div>
            </div>
        </div>
    </div>
    <update
        v-if="show"
        @update="updateInfo"
        v-model:accountName="accountName"
        v-model:name="name"
        v-model:sex="sex"
        v-model:password="password"
    >
    </update>
</template>

<style scoped>
#bottom{
    height: calc(100vh - 80px);
}
#bottom .left{
    height: 100%;
    width: 150px;
    float: left;
    background-color: rgb(56, 56, 136);
}
#bottom .listLeft{
    width: 100px;
    height: 500px;
    margin-left: 40px;
    margin-top: 100px;
}
#bottom .listLeft li{
    margin-top: 50px;
    color: white;
    cursor: pointer;
}
#bottom .right{
    width: calc(100vw - 150px);
    height: 100%;
    overflow: hidden;
    background-color: skyblue;
}
#bottom .info{
    width: 800px;
    margin: 50px auto;
}
#bottom .top{
    width: 100%;
    height: 30px;
}
#bottom .top h2{
    font-size: 30px;
    float: left;
}
#bottom .top button{
    width: 50px;
    height: 24px;
    float: right;
    color: #fff;
    background-color: blue;
    cursor: pointer;
}
#bottom .bot{
    width: 100%;
    margin-top: 80px;
}
#bottom .bot input{
    width: 740px;
    height: 40px;
    margin-top: 30px;
}
</style>
