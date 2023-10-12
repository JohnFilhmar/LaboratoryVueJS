<template>
    <Head/>
    <Body/>
    <Footer/>
</template>
<script>
import Head from '@/Arsha/Head.vue';
import Body from '@/Arsha/Body.vue';
import Footer from '@/Arsha/Footer.vue';
export default {
    name: 'Arsha',
    components : {
        Head,
        Body,
        Footer
    },
    mounted() {
        const scriptPaths = [
            'arsha/vendor/aos/aos.js',
            'arsha/vendor/bootstrap/js/bootstrap.bundle.min.js',
            'arsha/vendor/glightbox/js/glightbox.min.js',
            'arsha/vendor/isotope-layout/isotope.pkgd.min.js',
            'arsha/vendor/php-email-form/validate.js',
            'arsha/vendor/swiper/swiper-bundle.min.js',
            'arsha/vendor/waypoints/noframework.waypoints.js',
            'arsha/js/main.js',
        ];

        const loadScript = (path) => {
        return new Promise((resolve, reject) => {
            const script = document.createElement('script');
            script.src = path;
            script.onload = resolve;
            script.onerror = reject;
            document.body.appendChild(script);
        });
        };

        const loadScripts = async () => {
        try {
            await loadScript(scriptPaths[0]); // Load jQuery first
            for (let i = 1; i < scriptPaths.length; i++) {
            await loadScript(scriptPaths[i]);
            }
        } catch (error) {
            console.error('Failed to load scripts:', error);
        }
        };
        loadScripts();
    }
}
</script>
<style scoped>
    @import '@/assets/arsha/vendor/aos/aos.css';
    @import '@/assets/arsha/vendor/bootstrap/css/bootstrap.min.css';
    @import '@/assets/arsha/vendor/bootstrap-icons/bootstrap-icons.css';
    @import '@/assets/arsha/vendor/boxicons/css/boxicons.min.css';
    @import '@/assets/arsha/vendor/glightbox/css/glightbox.min.css';
    @import '@/assets/arsha/vendor/remixicon/remixicon.css';
    @import '@/assets/arsha/vendor/swiper/swiper-bundle.min.css';
    @import '@/assets/arsha/css/style.css';
</style>