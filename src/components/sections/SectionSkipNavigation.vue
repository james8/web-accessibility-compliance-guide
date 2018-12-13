<!--

-->

<template>
    <div id="section-skip-navigation">
        <h2>MI-4. Skip Navigation</h2>

        <p>
            Provide a link, either the very first or one of the first focusable item on the page, to allow the user to skip over all navigation content to the main content. Some pages contain a large navigation or a company image which makes users who use Screen Readers have to traverse though each navigation link before getting to the main content of the page. Adding a <span class="fancy">skip</span> link will help them get to the content faster.       
        </p>

        <note :type="'normal'">
            <p>
                To view the <span class="fancy">skip navigation link</span> for this page, go to the <a href="https://intranet.hawaiipublicschools.org/" target="_blank">root site</a> and tab once. The very first link will be focused and will take you to the main content of the site when pressed.
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
    export default class SectionSkipNavigation extends Vue {
        
    };
</script>

<style scoped>

</style>
