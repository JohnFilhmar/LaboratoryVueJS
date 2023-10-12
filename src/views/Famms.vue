<template>
    <div class="hero_area">
        <Head/>
        <Body/>
    </div>
        <Sections/>
        <Footer/>
</template>
<script>
import Head from '@/Famms/Head.vue';
import Body from '@/Famms/Body.vue';
import Sections from '@/Famms/Sections.vue';
import Footer from '@/Famms/Footer.vue';
export default {
    name: 'Famms',
    components : {
        Head,
        Body,
        Sections,
        Footer
    },
    mounted() {
        const scriptPaths = [
            'famms/js/jquery-3.4.1.min.js',
            'famms/js/popper.min.js',
            'famms/js/bootstrap.js'
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
    @import '@/assets/famms/css/bootstrap.css';
    @import '@/assets/famms/css/font-awesome.min.css';
    @import '@/assets/famms/css/style.css';
    @import '@/assets/famms/css/responsive.css';
</style>