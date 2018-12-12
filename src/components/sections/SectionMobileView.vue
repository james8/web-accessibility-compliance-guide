<!--

-->

<template>
    <div id="section-mobile-view">
        <h2>MI-8. Mobile View</h2>

        <p>
            Try to make the site as mobile-friendly as possible to give mobile users a pleasant experience when visiting the site. This can be done by making the site's width dynamically fit to the viewport of the device so there is no need to pan the page left or right to see all contents on the page. One thing to keep in mind when doing this is to make sure content is not cut-off or hidden due to the small screen size.      
        </p>

        <p>
            More information can be obtained by referring to the <a href="https://www.w3.org/TR/mobile-accessibility-mapping/" target="_blank">W3C article on Mobile Accessibility</a>.      
        </p>

        <note :type="'warning'" :title="'warning'">
            <p>
                DO NOT disable the default pinch-zoom option which allows a user to zoom in and out of the page (this is to allow visually imparied users to see content easier on their mobile device).
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
    export default class SectionMobileView extends Vue {
        
    };
</script>

<style scoped>

</style>
