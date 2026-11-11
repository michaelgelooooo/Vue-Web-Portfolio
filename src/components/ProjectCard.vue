<script setup>
import { defineProps } from "vue";

defineProps({
	project: Object,
});
</script>

<template>
	<div class="col-12 col-md-6 col-lg-4">
		<div class="card h-100 flex-row flex-sm-column overflow-hidden">
			<img :src="project.image" class="col-4 col-sm-12 p-0 img-fluid" alt="Project Photo" />
			<div class="card-body col-8 col-sm-12 d-flex flex-column p-2 p-lg-3">
				<h4 class="card-title">{{ project.title }}</h4>
				<p class="card-text d-none d-sm-block">{{ project.description }}</p>

				<div class="d-none d-sm-grid mt-auto">
					<a v-if="project.link" :href="project.link" class="btn project-button rounded-pill" target="_blank">View Project →</a>

					<button v-else class="btn project-button rounded-pill" disabled>Coming Soon</button>
				</div>

				<div class="d-block d-sm-none text-end p-0 m-0 mt-auto">
					<i class="fa-solid fa-arrow-right"></i>
				</div>
			</div>
		</div>
	</div>
</template>
