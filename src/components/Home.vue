<template>
    <section class="container" id="landing">
        <div class="row align-items-center">
            <div class="col-12 col-md-6 d-flex flex-column justify-content-center p-5">
                <h1 class="align-self-start mb-3 hello-hover">hello, world</h1>
                <div class="holographic-container">
                    <div class="holographic-card mb-3">
                        <p class="card-text">I’m Daimler Chrysler N. Lumbera, a full stack developer in training with a strong interest in building modern, user-focused web applications. I enjoy combining creativity with technical skills to develop interactive systems and meaningful digital solutions. Passionate about continuous learning, I aim to create applications that are both functional and impactful.</p>
                    </div>					
                </div>
            </div>
            <div class="col-12 col-md-6 d-flex justify-content-center">
                <div class="card id-card">
                    <img src="../assets/images/LUMBERA 1x1.JPG" class="card-img-top img-fluid rounded-circle p-5 mx-auto d-block" alt="Profile Image">
                    <div class="card-body justify-content-center">
                        <h3 class="card-title text-center">Daimler Chrysler N. Lumbera</h3>
                        <h5 class="card-title text-center mb-4">Full Stack Web Developer</h5>
                        <a :href="resumePdf" download="Daimler_Lumbera_Resume.pdf" target="_blank" class="cssbuttons-io text-decoration-none d-block mx-auto w-50 mb-3 text-center">
                            <span class="w-100 justify-content-center"><strong>View Resume</strong></span>
                        </a>
                        <a href="#projects" class="cssbuttons-io text-decoration-none d-block mx-auto w-50 text-center">
                            <span class="w-100 justify-content-center"><strong>View Projects</strong></span>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
    import resumePdf from '../assets/LUMBERA, Daimler - RESUME.pdf';
</script>
