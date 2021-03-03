<template>
	<div class="body-login">
		<p class="intro1">
			航康呼叫系统手自动切换 <br />密码：<input
				type="password"
				v-model="password"
				style="width: 40%; height: 40px"
			/>
			<button
				style="font-size: 80%; width: 70%; height: 50px"
				v-on:click="login"
			>
				点击登录
			</button>
		</p>
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
				.get("/project/agv.json") 	// 存放json的路径
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
.body-login {
	background-color: #61a1bc;
	position: absolute;
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;
	overflow-y: auto;
	font-size: 50px;
}
.intro1 {
	background-color: #61a1bc;
	font-size: 80%;
	color: Blue;
	text-align: center;
	border-radius: 20px;

	line-height: 150%;
	position: relative;
	width: 80%;
	height: 30%;
	border-radius: 5px;
	margin: 20% auto;
}
</style>
