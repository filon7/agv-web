<template>
	<div class="modal-bg" v-show="show">
		<div class="modal-container">
			<div class="modal-header">
				{{ title }}
			</div>
			<div class="modal-main">
				<slot></slot>
			</div>
			<div class="modal-footer">
				<el-button type="danger" round @click="hideModal">取消</el-button>
				<el-button type="success" round @click="submit">确认</el-button>
			</div>
		</div>
	</div>
</template>

<script>
export default {
    name: 'show-modal',
    props: {
        show: {
            type: Boolean,
            default: false
        },
        title: {
            type: String,
            default: ''
        },
    },
    methods: {
        hideModal() {
            this.$emit('hideModal')
        },

        submit() {
            this.$emit('submit')
        },
    }
}
</script>

<style scoped>
.modal-bg {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,.5);
    z-index: 10;
}
.modal-container {
    background: #fff;
    border-radius: 10px;
    overflow: hidden;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    font-size: 25px;
    font-weight: 900;
}
.modal-header {
    height: 56px;
    background: #409EFF;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: move;
    font-size: 25px;
    font-weight: 900;
}
.modal-footer {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 67px;
    border-top: 1px solid #ddd;
}
.modal-footer button {
    width: 200px;
    font-size: 35px;
    font-weight: 900;
}
.modal-main {
    padding: 15px 40px;
}
</style>





