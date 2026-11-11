<script setup>
defineProps({
	toolData: {
		type: Object,
		required: true,
	},
});
</script>

<template>
	<div class="col-12 col-md-6">
		<div class="card h-100 p-3">
			<h4 class="mb-2">
				<i :class="toolData.icon"></i>
				{{ toolData.category }}
			</h4>

			<div class="row justify-content-center g-1">
				<div v-for="tool in toolData.tools" :key="tool.id" class="col-6 col-lg-4">
					<div class="d-flex align-items-center gap-1 tool-card p-2">
						<i :class="tool.icon"></i>
						{{ tool.name }}
					</div>
				</div>
			</div>
		</div>
	</div>
</template>
