<!--

-->

<template>
    <div id="section-navigation">
        <h2>CI-1. Navigation</h2>

        <p>
            Ensure that <span class="fancy">ALL</span> navigation links (main menus & sub-menus) are accessible via both mouse <span class="fancy">AND</span> keyboard.
        </p>
        <p>
            Navigation menus are usually styled nicely with a mouse in mind, but often don't work well with just a keyboard.
        </p>

        <note :type="'warning'" :title="'warning'">
            <p>
                When creating navigation menus, it is often designed with a mouse or keyboard in mind and not touch.  For example, if a navigation's main menu items contain a link and also a dropdown submenu of links (made visible on focus/hover) access to the submenu items wont be possible on mobile devices.  This is because a user can only interact with touch on mobile devices and will trigger the link navigation on the main menu item.  So to accommodate for mouse, keyboard, and touch, it is best to create the main menu item as a non-link.
            </p>
            <p>
                It's also best to not have links which are hidden and become visible on mouse hover.  This is due to the fact that mobile user, who only have the capability of touch, may not be able to access these links.  Some hover capabilities may also be unreachable via keyboard navigation.
            </p>
        </note>

        <navigation-nc :link="'section-navigation'"></navigation-nc>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from "vue-property-decorator";

    import NavigationNc from "@/components/NavigationNc.vue";
    import Note from "@/components/Note.vue";

    @Component({
        components: {
            NavigationNc,
            Note
        }
    })
    export default class SectionNavigation extends Vue {
        
    };
</script>

<style scoped>

</style>

