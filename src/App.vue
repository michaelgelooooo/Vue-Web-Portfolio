<script setup>
import Contact from "./components/Contact.vue";
import Footer from "./components/Footer.vue";
import Landing from "./components/Landing.vue";
import Navbar from "./components/Navbar.vue";
import Projects from "./components/Projects.vue";
import Tools from "./components/Tools.vue";
</script>

<template>
	<Navbar />
	<main>
		<Landing />
		<Projects />
		<Tools />
        <Contact />
	</main>
    <Footer />
</template>
