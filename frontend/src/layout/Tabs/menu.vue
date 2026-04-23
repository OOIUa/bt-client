<template>
	<div class="flex items-center">
		<ul class="flex m-0">
			<li :class="{ active: $route.path === '/setting' }" @click="goTo('/setting')">
				<div class="flex bg-text">
					<bt-icon name="user" :color="$route.path === '/setting' ? 'var(--el-color-primary)' : 'var(--el-text-color-regular)'" size="16" class="z-1" />
				</div>
			</li>
			<li :class="{ active: $route.path === '/home' }" @click="goTo('/home')">
				<div class="flex bg-text">
					<bt-icon name="panel" :color="$route.path === '/home' ? 'var(--el-color-primary)' : 'var(--el-text-color-regular)'" size="16" class="z-1" />
					<span class="title">{{ pub.lang('面板') }}</span>
				</div>
			</li>
			<li :class="{ active: $route.path === '/xterm' }" @click="goTo('/xterm')">
				<div class="flex bg-text">
					<bt-icon name="xterm" :color="$route.path === '/xterm' ? 'var(--el-color-primary)' : 'var(--el-text-color-regular)'" size="16" class="z-1" />
					<span class="title">{{ pub.lang('终端') }}</span>
				</div>
			</li>
		</ul>
		<el-divider direction="vertical" class="menu-line"></el-divider>
	</div>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router'
import { pub } from '@utils/tools'

const router = useRouter()

const goTo = (path: string) => {
	router.push(path)
}
</script>

<style scoped lang="scss">
ul {
	padding: 0;
	height: 100%;
	color: var(--el-text-color-primary);
	display: flex;
	align-items: center;
	margin-left: 0.5rem;
	li {
		display: flex;
		align-items: center;
		height: 2.8rem;
		padding: 0 1rem;
		border-radius: 6px;
		margin-right: 0.5rem;
		position: relative;
		cursor: pointer;
		transition: all 0.2s ease;
		
		.bg-text {
			z-index: 1;
			display: flex;
			align-items: center;
			.title {
				font-size: 1.3rem;
				font-weight: 500;
				margin-left: 0.6rem;
			}
		}
		
		&:hover {
			background-color: var(--el-fill-color-light);
		}
		
		&.active {
			background-color: var(--el-color-primary-light-9);
			color: var(--el-color-primary);
			font-weight: 600;
			
			:deep(svg) {
				fill: var(--el-color-primary) !important;
				path { fill: var(--el-color-primary) !important; }
			}
		}
		
		&:last-child {
			margin-right: 0;
		}
	}
}
.menu-line {
	border-width: 1px;
	border-color: var(--el-border-color);
	height: 2rem;
	margin: 0 1rem;
}
</style>
