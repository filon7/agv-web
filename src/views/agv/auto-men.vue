<template>
	<div class="about">
		<h1>This is an about page</h1>
		<ShowModal :show="show" :title="title" @hideModal="hideModal" @submit="submit">
			<p>这里放弹窗的内容</p>
		</ShowModal>
	</div>
</template>

<script>
import ShowModal from "@/components/ShowModal.vue";

export default {
	data() {
		return {
			title: "系统提示",
			show: true,
		};
	},
	components: {
		ShowModal,
	},
	methods: {
		hideModal() {
			// 取消弹窗回调
			this.show = false;
		},

		submit() {
			// 确认弹窗回调
			this.show = false;
		},
	},
};
</script>

