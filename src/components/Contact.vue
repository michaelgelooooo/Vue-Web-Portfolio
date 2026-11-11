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
							<form>
								<div class="row gx-2">
									<div class="col-12 col-md-6 mb-3">
										<label for="name" class="form-label">
											Name
											<span class="text-danger" aria-hidden="true">*</span>
										</label>

										<input type="text" class="form-control" id="name" name="name" placeholder="What's your name?" autocomplete="name" required />
									</div>

									<div class="col-12 col-md-6 mb-3">
										<label for="email" class="form-label">
											Email
											<span class="text-danger" aria-hidden="true">*</span>
										</label>

										<input type="email" class="form-control" id="email" name="email" placeholder="Where can I reach you?" autocomplete="email" required />
									</div>
								</div>

								<div class="mb-3">
									<label for="inquiry" class="form-label">
										Inquiry Type
										<span class="text-danger" aria-hidden="true">*</span>
									</label>

									<select id="inquiry" name="inquiry" class="form-select" required>
										<option value="" selected disabled>Select an inquiry type</option>
										<option value="job-opportunity">Job Opportunity</option>
										<option value="freelance-project">Freelance Project</option>
										<option value="collaboration">Collaboration</option>
										<option value="general-inquiry">General Inquiry</option>
										<option value="other">Other</option>
									</select>
								</div>

								<div class="mb-4">
									<label for="message" class="form-label">
										Message
										<span class="text-danger" aria-hidden="true">*</span>
									</label>

									<textarea class="form-control" id="message" name="message" rows="5" placeholder="Tell me in detail how I can help you." required></textarea>
								</div>

								<button type="submit" class="btn w-100 py-2">
									<i class="fa-solid fa-paper-plane"></i>
									Send Message
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
