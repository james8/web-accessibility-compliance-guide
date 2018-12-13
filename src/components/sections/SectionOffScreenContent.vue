<!--

-->

<template>
    <div id="section-off-screen-content">
        <h2>MI-2. Off-Screen Content</h2>
            
            <p>Any element that is focusable (i.e. buttons, links, input fields, etc.) and is positioned outside of the page's view should not be able to be focused. If an element is intentially positioned off screen, apply a <span class="fancy">'tabindex="-1"' attribute</span> to make it non-focusable. </p>

        <h3>Off-Screen Focusable</h3>

        
        <button type="button" id="m2-focus-btn" class="focus-btn" @blur="FocusHere(0,$event);" @focus="FocusHere(1,$event);">Focus Here</button>
        &nbsp;&nbsp;&nbsp;
        <button type="button" id="m2-focus-btn1" class="focus-btn" @click="ToggleMenu(1,'')">Toggle Menu</button>
        <div id="m2-sidenav" class="sidenav sidenav-hidden">
            <span class="title">Menu Focusable</span>
            <button class="sidenav-btn" type="button" @click="ToggleMenu(0,'')">Close</button>
        </div>
        <div id="m2-backdrop" class="backdrop backdrop-hidden" @click="ToggleMenu(0,'')"></div>
        &nbsp;&nbsp;&nbsp;
        <button type="button" id="m2-focus-btn2" class="focus-btn" @blur="FocusHere(0,$event);" @focus="FocusHere(1,$event);">Focus Here</button>
       

        <note :type="'normal'">
            <p>
                For the example above, if you start the focus at the 1st button and <span class="fancy">tab</span> to the next buttons, you would expect to tab to <span class="fancy">Toggle Menu</span> - 2nd <span class="fancy">Focus Here</span>. But the tab order is 1st <span class="fancy">Focus Here - Toggle Menu - -</span> 2nd <span class="fancy">Focus Here</span>. The focus seems to disappear, but is actually on the hidden menu's button.
            </p>
            <p>
                To see the missing focus in action, do the following:
                <ol>
                    <li>Press the 1st <span class="fancy">Focus Here</span></li>
                    <li>Tab to <span class="fancy">Toggle Menu</span></li>
                    <li>Press spacebar (the menu will appear)</li>
                    <li>Tab to the next focus, which you will see is now on the <span class="fancy">Close</span> button in the menu</li>
                    <li>Tab to the next focus will now go to the 2nd <span class="fancy">Focus Here</span></li>
                </ol>
            </p>
        </note>

        <h3>Off-Screen Non-Focusable</h3>

        
        <button type="button" id="m2-focus-btna" class="focus-btn" @blur="FocusHere(0,$event);" @focus="FocusHere(1,$event);">Focus Here</button>
        &nbsp;&nbsp;&nbsp;
        <button type="button" id="m2-focus-btn1a" class="focus-btn" @click="ToggleMenu(1,'a')">Toggle Menu</button>
        <div id="m2-sidenava" class="sidenav sidenav-hidden">
            <span class="title">Menu Focusable</span>
            <button class="sidenav-btn" type="button" tabindex="-1" @click="ToggleMenu(0,'a')">Close</button>
        </div>
        <div id="m2-backdropa" class="backdrop backdrop-hidden" @click="ToggleMenu(0,'a')"></div>
        &nbsp;&nbsp;&nbsp;
        <button type="button" id="m2-focus-btn2a" class="focus-btn" @blur="FocusHere(0,$event);" @focus="FocusHere(1,$event);">Focus Here</button>
       

        <note :type="'normal'">
            <p>
                For the example above, each button is focused correctly since the hidden menu's button is marked as <span class="fancy">non-focusable</span> with the <span class="fancy">tabindex</span> attribute.
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
    export default class SectionOffScreenContent extends Vue {

        FocusHere(type: boolean, event: any): void {
            if (!type) event.target.innerHTML  = "Focus Here";
            else {
                event.target.innerHTML = "Focused";
            }
        }

        ToggleMenu(type: boolean, nf: string): void {
            if (!type) {
                (document.getElementById(`m2-sidenav${ nf }`) as HTMLElement).className = "sidenav sidenav-hidden";
                (document.getElementById(`m2-backdrop${ nf }`) as HTMLElement).className= "backdrop backdrop-hidden";
            } else {
                (document.getElementById(`m2-sidenav${ nf }`) as HTMLElement).className = "sidenav";
                (document.getElementById(`m2-backdrop${ nf }`) as HTMLElement).className= "backdrop";
            }
        }
        
    };
</script>

<style scoped>

    .focus-btn, .sidenav-btn{
        background-color: #f7f7f7;
        border: 1px solid #b9b9b9;
        cursor: pointer;
        height: 38px;
        width: 125px;
    }

    .focus-btn:hover, .sidenav-btn:hover {
        background-color: #e9e9e9;
        border-color: #9f9f9f;
    }

    .focus-btn:focus {
        border-color:rgba(0, 174, 255, 0.952);
        border-width: 2px;
    }

    .sidenav-btn:focus {
        background-color: #000;
        color: #fff;
    }

    .sidenav-hidden {
        -webkit-transform: translateX(-290px);
        transform: translateX(-290px);
        transition: -webkit-transform .5s ease;
        transition: transform .5s ease;
        transition: transform .5s ease,-webkit-transform .5s ease;
    }

    .sidenav {
        background-color: #536d79;
        color: #fff;
        width: 250px;
        padding: 20px;
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        z-index: 5;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
        -ms-flex-direction: column;
        flex-direction: column;
        transition: -webkit-transform .5s ease;
        transition: transform .5s ease;
        transition: transform .5s ease,-webkit-transform .5s ease;
    }

    .title {
        font-size: 24px;
        margin-bottom: 10px;
    }

    .backdrop-hidden {
        display: none;
    }
    .backdrop {
        background-color: rgba(0,0,0,.5);
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
    }

</style>

