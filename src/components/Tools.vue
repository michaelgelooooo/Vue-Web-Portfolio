<script setup>
import ToolCard from "./ToolCard.vue";
import tools from "../data/tools.json";
</script>

<template>
	<section id="tools">
		<div class="container p-4 p-md-5">
			<div class="row text-center text-md-start mb-4">
				<h2>
					<i class="fa-solid fa-code"></i>
					Core Technologies
				</h2>
				<p>A collection of technologies, frameworks, and tools I'm familiar with.</p>
			</div>

			<div class="row g-2 g-lg-4">
				<ToolCard v-for="tool in tools" :key="tool.id" :toolData="tool" />
			</div>
		</div>
	</section>
</template>
