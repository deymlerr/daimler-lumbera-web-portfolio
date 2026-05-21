<script setup>
    import AboutMe from './components/AboutMe.vue';
    import Home from './components/Home.vue';
    import Projects from './components/Projects.vue';
    import Skills from './components/Skills.vue';
    import Tools from './components/Tools.vue';
    import Contact from './components/Contact.vue';
    import NavBar from './components/NavBar.vue';
    import Footer from './components/Footer.vue';
</script>

<template>
    <div id="top"></div>
    <NavBar />
    <Home />
    <Projects />
    <AboutMe />
    <Skills />
    <Tools />
    <Contact />
    <Footer />
    <a href="#top" class="back-to-top position-fixed bottom-0 end-0 m-4 shadow" aria-label="Back to top">
        <svg class="svgIcon" viewBox="0 0 384 512" xmlns="http://www.w3.org/2000/svg">
            <path d="M214.6 41.4c-12.5-12.5-32.8-12.5-45.3 0l-160 160c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0L160 141.2V448c0 17.7 14.3 32 32 32s32-14.3 32-32V141.2L329.4 246.6c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3l-160-160z"></path>
        </svg>
    </a>
</template>
