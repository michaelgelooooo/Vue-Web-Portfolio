<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import axios from "axios";
import { Notyf } from "notyf";
import "notyf/notyf.min.css";

const notyf = new Notyf();

const WEB3FORMS_ACCESS_KEY = "c9082d03-0647-4e26-ab1b-3a5090497c52";
const SITE_KEY = "6LcHkBouAAAAAM_zYaY-KTUH0TJT1WVd0D-ApyEe";

const subject = "Message from Portfolio Contact Form";

const name = ref("");
const email = ref("");
const inquiry_type = ref("");
const message = ref("");

const isLoading = ref(false);

const submitForm = async () => {
	if (!recaptchaToken.value) {
		notyf.error("Please verify that you are not a robot.");
		return;
	}

	isLoading.value = true;

	try {
		const response = await axios.post(
			"https://api.web3forms.com/submit",
			{
				access_key: WEB3FORMS_ACCESS_KEY,
				subject: subject,
				name: name.value,
				email: email.value,
                inquiry_type: inquiry_type.value,
				message: message.value,
			},
			{
				headers: {
					"Content-Type": "application/json",
					Accept: "application/json",
				},
			},
		);

		const result = response.data;

		if (result.success) {
			notyf.success("Message Sent!");

			name.value = "";
			email.value = "";
			inquiry_type.value = "";
			message.value = "";
		}
	} catch (error) {
		notyf.error("Failed to send message!");
	} finally {
		isLoading.value = false;
	}
};

const recaptchaContainer = ref(null);
const recaptchaWidgetId = ref(null);
const recaptchaToken = ref("");

function onRecaptchaSuccess(token) {
	recaptchaToken.value = token;
}

function onRecaptchaExpired() {
	recaptchaToken.value = "";
}

function renderRecaptcha() {
	if (!window.grecaptcha) {
		console.error("reCAPTCHA not loaded");
		return;
	}

	recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
		sitekey: SITE_KEY,
		size: "normal",
		callback: onRecaptchaSuccess,
		"expired-callback": onRecaptchaExpired,
	});
}

function resetRecaptcha() {
	if (recaptchaWidgetId.value !== null) {
		window.grecaptcha.reset(recaptchaWidgetId.value);
		recaptchaToken.value = "";
	}
}

onMounted(() => {
	const interval = setInterval(() => {
		if (window.grecaptcha && window.grecaptcha.render) {
			renderRecaptcha();
			clearInterval(interval);
		}
	}, 100);

	onBeforeUnmount(() => {
		clearInterval(interval);
	});
});
</script>

<template>
	<section id="contact">
		<div class="container p-4 p-md-5">
			<div class="row text-center text-md-start mb-4">
				<h2 id="contact-title"><i class="fa-regular fa-message"></i> Get In Touch</h2>
				<p>Whether it's a project, opportunity, or just a conversation, I'd love to hear from you.</p>
			</div>

			<div class="row g-4">
				<div class="col-12 col-lg-6">
					<div class="card p-2">
						<div class="card-body">
							<form @submit.prevent="submitForm">
								<div class="row gx-2">
									<div class="col-12 col-md-6 mb-3">
										<label for="name" class="form-label">
											Name
											<span class="text-danger" aria-hidden="true">*</span>
										</label>

										<input v-model="name" type="text" class="form-control" id="name" name="name" placeholder="What's your name?" autocomplete="name" required />
									</div>

									<div class="col-12 col-md-6 mb-3">
										<label for="email" class="form-label">
											Email
											<span class="text-danger" aria-hidden="true">*</span>
										</label>

										<input v-model="email" type="email" class="form-control" id="email" name="email" placeholder="Where can I reach you?" autocomplete="email" required />
									</div>
								</div>

								<div class="mb-3">
									<label for="inquiry" class="form-label">
										Inquiry Type
										<span class="text-danger" aria-hidden="true">*</span>
									</label>

									<select v-model="inquiry_type" id="inquiry" name="inquiry" class="form-select" required>
										<option value="" selected disabled>Select an inquiry type</option>
										<option value="job-opportunity">Job Opportunity</option>
										<option value="freelance-project">Freelance Project</option>
										<option value="collaboration">Collaboration</option>
										<option value="general-inquiry">General Inquiry</option>
										<option value="other">Other</option>
									</select>
								</div>

								<div class="mb-3">
									<label for="message" class="form-label">
										Message
										<span class="text-danger" aria-hidden="true">*</span>
									</label>

									<textarea v-model="message" class="form-control" id="message" name="message" rows="5" placeholder="Tell me in detail how I can help you." required></textarea>
								</div>

								<div class="d-flex justify-content-center w-100 mb-4">
									<div ref="recaptchaContainer"></div>
								</div>

								<button type="submit" class="btn w-100 py-2" :disabled="isLoading">
									<i class="fa-solid fa-paper-plane"></i>
									{{ isLoading ? "Sending Message..." : "Send Message" }}
								</button>
							</form>
						</div>
					</div>
				</div>

				<div class="col-12 col-lg-6">
					<div class="card p-2">
						<div class="card-body">
							<h4>
								<i class="fa-solid fa-location-dot"></i>
								Tokyo, Japan
							</h4>

							<hr />

							<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d4372.794224726038!2d139.7258655767446!3d35.66202667259348!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x60188b79dc0fffff%3A0xa5ebbccf66c62dbb!2z44K444O844OX44Op44ix77yIR2VlUGx1cywgSW5jLu-8iQ!5e1!3m2!1sen!2sph!4v1790669306556!5m2!1sen!2sph" style="border: 0" allowfullscreen loading="lazy"> </iframe>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>
