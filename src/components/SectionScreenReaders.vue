<!--

-->

<template>
    <div id="section-screen-readers">
        <h2>Screen Readers</h2>

        <p>
            A useful tool to use make sure that your site is compliant for visually impaired users is to use a Screen Reader.  This is good for debugging since we can hear exactly what a visually impaired user would hear.  There are free Screen Readers available for both Mac and Windows platforms.
        </p>
        <p>
            Mac's built-in Screen Reader is <a href="https://help.apple.com/voiceover/info/guide/10.12/" target="_blank">VoiceOver</a>
        </p>
        <p>
            A free Screen Reader that can be used on Windows is <a href="https://www.nvaccess.org/" target="_blank">NVDA</a>
        </p>

        <note :type="'tip'" :title="'tip'">
            <p>
                You do not need to donate in order to use the NVDA software.
            </p>
        </note>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from "vue-property-decorator";

    import Note from "@/components/Note.vue";

    @Component({
        components: {
            Note
        }
    })
    export default class SectionScreenReaders extends Vue {
        
    };
</script>

<style scoped>

</style>
