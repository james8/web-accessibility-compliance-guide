<!--

-->

<template>
    <div id="section-focusable-elements">
        <h2>MI-1. Focusable Elements</h2>

        <p>
            Make sure that any element that is focusable (i.e. buttons, links, input fields, etc.) are made clear that they are being focused on. Making a focusable element distinguishable when focused is helpful for users to know where they currently are on the page. This is especially helpful when switching back to the page and knowing where you left off. 
        </p>

        <note :type="'tip'" :title="'tip'">
            <p>
                Most focusable elements have a blue outline when focused by default (although it may be ugly, it is recommended to never remove it unless you add custom CSS to make it noticable to a user that the element is currently focused).
            </p>
        </note>

        <h3>Non-Distinguished Focus:</h3>
        <p>
        <button type="button" id="m1-focus-btn1" class="focus-btn" @blur="FocusHere(0,$event);" @focus="FocusHere(1,$event);">Focus Here</button>
        &nbsp;&nbsp;&nbsp;
        <button type="button" id="m1-focus-btn1a" class="focus-btn" @blur="FocusHere(0,$event);" @focus="FocusHere(1,$event);">Focus Here</button>
        </p>
        

        <h3>Non-Distinguished Focus:</h3>
        <p>
        <button type="button" id="m1-focus-btn2" class="focus-btn-distinguished" @blur="FocusHere(0,$event);" @focus="FocusHere(1,$event);">Focus Here</button>
        &nbsp;&nbsp;&nbsp;
        <button type="button" id="m1-focus-btn2a" class="focus-btn-distinguished" @blur="FocusHere(0,$event);" @focus="FocusHere(1,$event);">Focus Here</button>
        </p>        

        <note :type="'normal'">
            <p>
                Note that the button says <span class="fancy">'Focused'</span> when the button is focused, and <span class="fancy">'Focus Here'</span> when not. If it weren't for the button's title, we would not know what is being focused at the moment for the non-distinguised example. 
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
    export default class SectionFocusableElements extends Vue {

        FocusHere(type: boolean, event: any): void {
            if (!type) event.target.innerHTML  = "Focus Here";
            else {
                event.target.innerHTML = "Focused";
            }
        }
        
    };
</script>

<style scoped>

    .focus-btn, .focus-btn-distinguished{
        background-color: #f7f7f7;
        border: 1px solid #b9b9b9;
        cursor: pointer;
        height: 38px;
        width: 125px;
    }

    .focus-btn:hover, .focus-btn-distinguished:hover {
        background-color: #e9e9e9;
        border-color: #9f9f9f;
    }
    

    .focus-btn:focus {
        border-color: #9f9f9f;
        outline-color: #9f9f9f
    }

    .focus-btn-distinguished:focus {
        border-color:rgba(0, 174, 255, 0.952);
        border-width: 2px;
    }

</style>

