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

        <h3>Only Mouse Accessible:</h3>
        <navigation-nc :link="'section-navigation'"></navigation-nc>

        <note :type="'normal'">
            <p>
                The navigation menu presented above is only mouse accessible.  If you start the browser's focus on the <span class="fancy">'Focus Here'</span> button and try to navigate through the menus with a keyboard, you will not be able to reach the submenus since they are only shown when the associated menu is focused.
            </p>
        </note>

        <h3>Mouse & Keyboard Accessible:</h3>
        <navigation :link="'section-navigation'"></navigation>

        <note :type="'normal'">
            <p>
                The navigation menu presented above is accessible via mouse and keyboard.  If you start the browser's focus on the <span class="fancy">'Focus Here'</span> button, all menu and submenus can be accessed using the arrow keys on the keyboard.  The <span class="fancy">Enter</span> key is used to open the submenus and the <span class="fanc">Escape</span> key is used to get out of the submenus and back to the main menus.  This example is just one way to make a navigation which is compliant and may not be the best way to be implemented.
            </p>
        </note>

        <note :type="'warning'">
            <p>
                For this example, if using the NVDA Screen Reader (not sure if VoiceOver is the same) using the arrow keys will read the word's characters line-by-line instead of traversing through the navigation.  To get around this, a <span class="fancy">role="application"</span> was added to prevent the Screen Reader from intercepting the arrow key presses.  Doing this may not be the best idea since the default behavior for arrow keys on the Screen Reader is supposed to help users spell out words if they do not understand what is being read.
            </p>
        </note>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from "vue-property-decorator";

    import Navigation from "@/components/Navigation.vue";
    import NavigationNc from "@/components/NavigationNc.vue";
    import Note from "@/components/Note.vue";

    @Component({
        components: {
            Navigation,
            NavigationNc,
            Note
        }
    })
    export default class SectionNavigation extends Vue {
        
    };
</script>

<style scoped>

</style>

