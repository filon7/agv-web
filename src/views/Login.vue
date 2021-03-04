<template>
	<div class="login-bg">
		<div class="body-login">
			<div>
				<p>航康呼叫系统手自动切换</p>
				<p>密码：<el-input style="width: 50%" size="medium" type="password" placeholder="请输入内容" v-model="password" clearable > </el-input> </p>
				<el-button style="font-size: 80%; width: 70%; height: 50px" type="success" round @click="login" >点击登录</el-button>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "Login",
	data() {
		return {
			password: "",
		};
	},
	methods: {
		login() {
			this.$axios
				.get("/project/agv.json") // 存放json的路径
				.then((res) => {
					console.log(res.data.password);
					if (this.password == res.data.password) {
						this.$router.push("/AGV/auto-men");
					} else {
						alert("密码错误！");
						this.password = "";
					}
				})
				.catch(() => {
					alert("未找到配置文件！");
				});
		},
	},
};
</script>

<style scoped>
.login-bg {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: #61a1bc;
}

.body-login {
	border-radius: 10px;
	overflow: hidden;
	position: fixed;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	font-size: 30px;
	font-weight: 900;
}
</style>
