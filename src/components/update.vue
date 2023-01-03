<template>
    <div class="box">
        <div class="modal">
            <!-- header -->
            <div class="header">
                <p class="title">个人信息</p>
                <p class="close" @click="bindConfirm">x</p>
            </div>
            <!-- 内容区域 -->
            <div class="content">
                <div>
                    账号名:<input type="text" v-model="AccountName" /><br />
                    姓&emsp;名:<input type="text" v-model="Name" /><br />
                </div>
                <div>
                    性&emsp;别:<select v-model="Sex">
                        <option value="男">男</option>
                        <option value="女">女</option></select
                    ><br />
                    密&emsp;码:<input type="text" v-model="Password" /><br />
                </div>
            </div>
            <!-- 底部区域 -->
            <div class="footer">
                <button @click="bindConfirm">确定</button>
                <button @click="bindConfirm">取消</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['accountName', 'name', 'sex', 'password'],
    emits: ['update:accountName', 'update:name', 'update:sex', 'password'],
    methods: {
        bindConfirm() {
            this.$emit('update')
        },
    },
    computed: {
        AccountName: {
            get() {
                return this.accountName
            },
            set(newValue) {
                this.$emit('update:accountName', newValue)
            },
        },
        Name: {
            get() {
                return this.name
            },
            set(newValue) {
                this.$emit('update:name', newValue)
            },
        },
        Sex: {
            get() {
                return this.sex
            },
            set(newValue) {
                this.$emit('update:sex', newValue)
            },
        },
        Password: {
            get() {
                return this.password
            },
            set(newValue) {
                this.$emit('update:password', newValue)
            },
        },
    },
}
</script>

<style scoped>
.box {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(19, 19, 19, 0.4);
}
.modal {
    width: 600px;
    height: 400px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    background-color: rgb(246, 244, 244);
    display: flex;
    flex-direction: column;
}
 
.modal .header {
    display: flex;
    height: 30px;
    background-color: rgb(64, 157, 239);
    justify-content: space-between;
    padding: 15px;
}
.modal .header .close:hover {
    cursor: pointer;
    color: red;
}
.modal .content {
    flex: 1;
    padding: 20px;
}
.modal .content div:first-child{
    float: left;
}
.modal .content div:last-child{
    float: right;
}
.modal .content input{
    width: 150px;
    height: 25px;
    margin-top: 30px;
}
.modal .content select{
    width: 152px;
    height: 29px;
    margin-top: 30px;
}
.modal .footer {
    height: 40px;
    line-height: 40px;
    text-align: right;
    background-color: rgb(213, 224, 224);
}
.modal .footer button {
    width: 100px;
    height: 30px;
    line-height: 30px;
    text-align: center;
    border: none;
    outline: none;
    background-color: rgb(55, 71, 77);
    color: white;
    margin-right: 10px;
}
.modal .footer button:hover {
    cursor: pointer;
    background-color: rgb(19, 67, 86);
}

</style>
