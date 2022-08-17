<template>
	<div class="flow">
		<div class="name_wrapper">
			<div class="name">名称</div>
		</div>
		<div class="action_wrapper"><Action ref="actionRef" /></div>
		<div class="panel_wrapper"><Panel ref="panelRef" /></div>
		<div class="scene_wrapper"><Scene ref="sceneRef" /></div>
		<div class="tool_wrapper"><Tool ref="toolRef" /></div>
	</div>
</template>

<script>
import Action from "./controls/Action";
import Panel from "./controls/Panel";
import Scene from "./controls/Scene";
import Tool from "./controls/Tool";
export default {
	name: "flow",

	components: { Action, Panel, Scene, Tool },
};
</script>

<style scoped lang="less">
.flow {
	background: url("./images/bg.png") 0 0 repeat;
	position: fixed;
	top: 0;
	bottom: 0;
	left: 0;
	right: 0;
	overflow: hidden;
	z-index: 100;
	margin: auto;
	.name_wrapper {
		position: absolute;
		margin-top: 20px;
		margin-left: 10px;
		width: 100%;
		text-align: center;
		.name {
			color: #ffffff;
			font-size: 16px;
			font-weight: 500;
		}
	}
}
</style>
