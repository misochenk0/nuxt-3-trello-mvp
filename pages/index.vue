<template>
	<h1>Home page</h1>
	<h2>Recently viewed</h2>
	<h2>Workspaces</h2>
	<input type="text" v-model="newWorkspaceName">
	<button @click="createWorkspace">Create a workspace</button>
	<ul class="workspace-list">
		<li v-for="workspace in workspaceList" :key="workspace.id" class="workspace-card">
			{{workspace.id}}: {{workspace.name}}
		</li>
	</ul>
</template>

<script lang="ts" setup>
	import {ref} from "vue"

	interface Workspace {
		id: Number,
		name: String
	}

	const newWorkspaceName = ref("");
	const workspaceList = ref<Workspace[]>([])
	const createWorkspace = () => {
		const randomId = Math.floor(Math.random() * 100);

		workspaceList.value.push({
			id: randomId,
			name: newWorkspaceName.value
		})
	}
</script>

<style>
	.workspace-card {
		display: block;
		border: 2px solid #222;
		border-radius: 4px;
		padding: 2rem;
		margin-bottom: 1rem;
	}

	.workspace-list {
		margin-left: 0;
		padding: 0;
	}
</style>