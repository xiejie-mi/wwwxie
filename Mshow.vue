<template>
    <div>
        <h1>账号密码登录</h1>
        <table align="center">
            <!--            表格形式-->

            <tr>用户名：<input v-model="name" type="input"></tr>
            <tr>密码：<input v-model="pwd" type="password"></tr>

            <tr><router-link :to="'Mtable'"><button @click="sub()">注册</button></router-link></tr>
            <!--            注册方法-->

        </table>
    </div>
</template>

<script>
    export default {
        name: "Mshow",
        data(){
            return{
                data:'',
                name:'',
                pwd :'',
                // 定义变量
            }
        },
        methods:{
            sub(){
                var _this=this;
                // 申明this
                const  params =  new URLSearchParams();
                // 调用函数
                params.append('name',_this.name);
                params.append('pwd',_this.pwd);
                // 添加变量

                this.$axios.post('/api/api/mlogin',params)
                // 调用后台接口
                    .then(function (response) {
                        console.log(response);
                        // 打印结果
                        if(response.code==0){
                            // 判断是否添加成功
                            alert('登陆成功');
                            _this.$router.Location('Mshow')
                            // 跳转地址
                        }
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
            }
        }
    }
</script>

<style scoped>

</style>