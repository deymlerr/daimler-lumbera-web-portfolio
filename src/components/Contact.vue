<script setup>
	import { ref, onMounted, onBeforeUnmount } from 'vue';

	import { Notyf } from 'notyf';
	import 'notyf/notyf.min.css';

	const notyf = new Notyf();

	const WEB3FORMS_ACCESS_KEY = "034de545-8c02-425b-bb4f-50090be8892b";

	const name = ref("");
	const email = ref("");
	const subject = ref("");
	const message = ref("");

	const isLoading = ref(false);


	const submitForm = async() => {

		if(!recaptchaToken.value) {
			notyf.error('Please verify that you are not a robot.');
			return;
		}

		isLoading.value = true;

		try {

			const response = await fetch("https://api.web3forms.com/submit", {
				method: "POST",
				headers: {
					"Content-Type": "application/json",
					Accept: "application/json"
				},
				body: JSON.stringify({
					access_key: WEB3FORMS_ACCESS_KEY,
					subject: subject.value,
					name: name.value,
					email: email.value,
					message: message.value
				})
			});

			const result = await response.json();

			if(result.success) {
				console.log(result)

				isLoading.value = false;
				name.value = "";
				email.value = "";
				subject.value = "";
				message.value = "";
				notyf.success("Message sent!");
			} else {
				isLoading.value = false;
				notyf.error(result.message || "Failed to send message");
			}

		} catch(error) {
			console.log(error);

			isLoading.value = false;
			notyf.error("Failed to send message");

		} finally {

			resetRecaptcha();
		}
	}

	/*recaptcha integration*/

	const SITE_KEY = '6LeGDPUsAAAAAALCoIr-G-tw7LNlXcPHdldgrQIC';

	const recaptchaContainer = ref(null);
	const recaptchaWidgetId = ref(null);
	const recaptchaToken = ref('');


	function onRecaptchaSuccess(token) {
		recaptchaToken.value = token;
	}

	function onRecaptchaExpired() {
		recaptchaToken.value = '';
	}

	function renderRecaptcha() {
		if(!window.grecaptcha) {
			console.error('reCAPTCHA not loaded');
			return;
		}

		recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
			sitekey: SITE_KEY,
			size: 'normal',
			callback: onRecaptchaSuccess,
			'expired-callback': onRecaptchaExpired
		});
	}

	function resetRecaptcha() {
		if(recaptchaWidgetId.value !== null) {
			window.grecaptcha.reset(recaptchaWidgetId.value);
			recaptchaToken.value = '';
		}
	}

	let recaptchaInterval = null;

	onMounted(() => {
		recaptchaInterval = setInterval(() => {
			if(window.grecaptcha && window.grecaptcha.render) {
				renderRecaptcha();
				clearInterval(recaptchaInterval);
			}
		}, 100);
	})

	onBeforeUnmount(() => {
		if(recaptchaInterval) {
			clearInterval(recaptchaInterval);
		}
	})

</script>

<template>
    <section class="container pb-5" id="contact">
        <h1>Contact Me</h1>
        <div class="row">
            <!-- Contact Information -->
            <div class="col-12 col-lg-6 d-flex flex-column justify-content-center pb-5" id="info">
                <!-- LinkedIn -->
                <a href="https://www.linkedin.com/in/daimler-chrysler-lumbera-b36930319/" target="_blank" class="holo-card d-block">
                    <div class="col-6 col-sm-12">
                        <div class="row g-0 align-items-center">
                        <div class="col-md-2">
                            <div class="logo-box">
                            <img src="https://cdn-icons-png.flaticon.com/512/1384/1384014.png" class="img-fluid p-4" alt="...">
                            </div>
                        </div>
                        <div class="col-md-10">
                            <div class="card-body">
                            <h5 class="card-title">Daimler Chrysler N. Lumbera</h5>
                            </div>
                        </div>
                        </div>
                    </div>	
                </a>
                <!-- GitHub -->
                <a href="https://github.com/deymlerr" target="_blank" class="holo-card d-block">
                    <div class="col-6 col-sm-12">
                        <div class="row g-0 align-items-center">
                        <div class="col-md-2">
                            <div class="logo-box">
                            <img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" class="img-fluid p-4" alt="...">
                            </div>
                        </div>
                        <div class="col-md-10">
                            <div class="card-body">
                            <h5 class="card-title">deymlerr</h5>
                            </div>
                        </div>
                        </div>
                    </div>	
                </a>
                <!-- Email -->
                <div class="holo-card d-block">
                    <div class="col-6 col-sm-12">
                        <div class="row g-0 align-items-center">
                        <div class="col-md-2">
                            <div class="logo-box">
                            <img src="https://cdn-icons-png.flaticon.com/512/3178/3178158.png" class="img-fluid p-4" alt="...">
                            </div>
                        </div>
                        <div class="col-md-10">
                            <div class="card-body">
                            <h5 class="card-title">daimler.natividad@gmail.com</h5>
                            </div>
                        </div>
                        </div>
                    </div>	
                </div>
                <!-- Phone Number -->
                <div class="holo-card d-block">
                    <div class="col-6 col-sm-12">
                        <div class="row g-0 align-items-center">
                        <div class="col-md-2">
                            <div class="logo-box">
                            <img src="https://icons.veryicon.com/png/o/miscellaneous/yunrenui-original-ui-of-fool-cloud/phone-circle.png" class="img-fluid p-4" alt="...">
                            </div>
                        </div>
                        <div class="col-md-10">
                            <div class="card-body">
                            <h5 class="card-title">+63 947 714 0104</h5>
                            </div>
                        </div>
                        </div>
                    </div>	
                </div>
                <!-- Location -->
                <div class="holo-card col-6 col-sm-12">
                    <div class="row g-0 align-items-center">
                    <div class="col-md-2">
                        <div class="logo-box">
                        <img src="https://cdn-icons-png.flaticon.com/512/484/484167.png" class="img-fluid p-4" alt="...">
                        </div>
                    </div>
                    <div class="col-md-10">
                        <div class="card-body">
                        <h5 class="card-title">Metro Manila, Philippines</h5>
                        </div>
                    </div>
                    </div>
                </div>
            </div>
            <!-- Form -->
            <div class="card col-12 col-md-8 col-lg-6 mx-auto contact-card">
                <div class="card-body p-4">
                
                <form id="contactForm" @submit.prevent="submitForm">
                    
                    <div class="mb-3">
                    <label for="nameInput" class="form-label">Name</label>
                    <input v-model="name" type="text" class="form-control" id="nameInput" placeholder="John Zenless" required>
                    </div>

                    <div class="mb-3">
                    <label for="emailInput" class="form-label">Email</label>
                    <input v-model="email" type="email" class="form-control" id="emailInput" placeholder="name@example.com" required>
                    </div>
                    
                    <div class="mb-3">
                    <label for="subjectInput" class="form-label">Subject</label>
                    <input v-model="subject" type="text" class="form-control" id="subjectInput" placeholder="Web Project Inquiry" required>
                    </div>
                    
                    <div class="mb-4">
                    <label for="messageInput" class="form-label">Message</label>  
                    <textarea v-model="message" class="form-control" id="messageInput" placeholder="Your message here..." rows="4" required></textarea>
                    </div>
                    
                    <div class="d-flex justify-content-end">
                    <button type="submit" id="submitBtn" class="submit-btn mt-3" :disabled="isLoading">
                        <div class="svg-wrapper-1">
                        <div class="svg-wrapper">
                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24">
                            <path fill="none" d="M0 0h24v24H0z"></path>
                            <path fill="currentColor" d="M1.946 9.315c-.522-.174-.527-.455.01-.634l19.087-6.362c.529-.176.832.12.684.638l-5.454 19.086c-.15.529-.455.547-.679.045L12 14l6-8-8 6-8.054-2.685z"></path>
                            </svg>
                        </div>
                        </div>
                        <span>{{isLoading ? "Sending..." : "Submit"}}</span>
                    </button>
                    </div>
                    <div class="d-flex justify-content-end mt-2">
                        <div ref="recaptchaContainer"></div>
                    </div>
                </form>
                </div>
            </div>			
        </div>
    </section>
</template>

