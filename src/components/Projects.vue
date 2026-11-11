<script setup>
import ProjectCard from "./ProjectCard.vue";
import projects from "../data/projects.json";
</script>

<template>
	<section id="projects">
		<div class="container p-4 p-md-5">
			<div class="row text-center text-md-start mb-3">
				<h2><i class="fa-solid fa-file-code"></i> Featured Projects</h2>
				<p>Projects that showcase my skills, creativity, and problem-solving.</p>
			</div>

			<div class="row g-2">
                <ProjectCard
                    v-for="project in projects"
                    :key="project.id"
                    :project="project"
                />
            </div>
		</div>
	</section>
</template>
