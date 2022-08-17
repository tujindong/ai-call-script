<template>
	<div class="tool">
		<div class="tool_setting" v-show="!isToolBarVisible" @click="isToolBarVisible = true">
			<a-icon type="setting" :style="{ fontSize: '24px' }" />
		</div>
		<div class="tool_action" v-show="isToolBarVisible">
			<div class="slider_area">
				<a-icon
					@click="handleScaleChange(1)"
					type="zoom-in"
					:style="{
						marginBottom: '5px',
						fontSize: '19px',
						cursor: 'pointer',
						color: 'rgb(138, 198, 255)',
					}"
				/>
				<a-slider vertical v-model="scaleValue" />
				<a-icon
					@click="handleScaleChange(-1)"
					type="zoom-out"
					:style="{
						marginTop: '5px',
						fontSize: '19px',
						cursor: 'pointer',
						color: 'rgb(138, 198, 255)',
					}"
				/>
			</div>

			<a-icon
				type="drag"
				@click="handleDragChange"
				:style="{
					marginTop: '20px',
					fontSize: '19px',
					cursor: 'pointer',
					color: isDragActive ? 'yellow' : 'rgb(138, 198, 255)',
				}"
			/>

			<a-icon
				type="border-outer"
				@click="handleDrageReset"
				:style="{
					marginTop: '20px',
					fontSize: '19px',
					cursor: 'pointer',
					color: 'rgb(138, 198, 255)',
				}"
			/>

			<a-popover placement="right">
				<template slot="content">
					<div>拖动：长按空格 + 左键</div>
					<div>复制：Alt + C</div>
					<div>粘贴：Alt + V</div>
				</template>
				<template slot="title">
					<span>快捷键说明</span>
				</template>
				<a-icon
					type="question-circle"
					:style="{
						marginTop: '20px',
						fontSize: '19px',
						cursor: 'pointer',
						color: 'rgb(138, 198, 255)',
					}"
				/>
			</a-popover>

			<a-icon
				@click="isToolBarVisible = false"
				type="left-circle"
				:style="{
					marginTop: '20px',
					fontSize: '18px',
					cursor: 'pointer',
					color: 'rgb(138, 198, 255)',
				}"
			/>
		</div>
	</div>
</template>

<script>
export default {
	name: "Tool",

	data() {
		return {
			isToolBarVisible: true,
			isDragActive: false,
			scaleValue: 100,
		};
	},

	methods: {
		//改变流程图大小
		handleScaleChange() {},

		//拖拽
		handleDragChange() {},

		//拖拽重置
		handleDrageReset() {},
	},
};
</script>

<style scoped lang="less">
.tool {
	.tool_setting {
		display: inline-block;
		width: 24px;
		height: 24px;
		position: absolute;
		bottom: 40px;
		left: 20px;
		cursor: pointer;
		color: rgb(138, 198, 255);
		animation: spin 3s linear infinite;
		@-webkit-keyframes spin {
			0% {
				-webkit-transform: rotate(0deg);
			}

			to {
				-webkit-transform: rotate(1turn);
			}
		}

		@keyframes spin {
			0% {
				transform: rotate(0deg);
			}

			to {
				transform: rotate(1turn);
			}
		}
	}
	.tool_action {
		display: flex;
		align-content: center;
		flex-direction: column;
		width: 39px;
		padding: 20px 0;
		background: rgba(255, 255, 255, 0.1);
		border-radius: 3px;
		position: fixed;
		left: 10px;
		bottom: 40px;
		color: rgb(138, 198, 255);
		-webkit-animation-duration: 1s;
		animation-duration: 1s;
		-webkit-animation-fill-mode: both;
		animation-fill-mode: both;
		-webkit-animation-name: fadeInLeft;
		animation-name: fadeInLeft;

		@keyframes fadeInLeft {
			0% {
				opacity: 0;
				transform: translateX(0);
			}
			to {
				opacity: 1;
				transform: translateX(10px);
			}
		}
		.slider_area {
			display: flex;
			justify-content: center;
			align-items: center;
			flex-direction: column;
			height: 120px;
			width: 100%;
			.ant-slider {
				height: 100px;
			}
		}
	}
}
</style>
