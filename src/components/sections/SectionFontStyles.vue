<!--

-->

<template>
    <div id="section-font-styles">
        <h2>MI-7. Font Styles</h2>

        <p>
            Make sure that all text are a reasonable size and typeface (or font family) so they can be easily read by all users.     
        </p>

        <note :type="'tip'" :title="'tip'">
            <p>
                Try to avoid the use of text that are included in images since they can become distorted when enlarging the image making the text difficult to read.
            </p>
            <p>            
                Try to avoid <span class="fancy">blinking</span> or <span class="fancy">moving text</span>.
            </p>
            <p>
                For more help, see <a href="https://webaim.org/techniques/fonts/" target="_blank">WebAIM's Fonts article</a>.
            </p>
        </note>

        <h3>Font Size:</h3>

        <p>
            All text, besides <span class="fancy">captions</span> and <span class="fancy">image text</span> must be able to be resized without assistive technology up to 200% without the loss of any content or functionality. It is recommended that when defining text size, relative sizes (i.e. <span class="fancy">ems</span>) should be used instead of absolute sizes (i.e. <span class="fancy">pixels</span>).            
        </p>

        <p>
            There doesn't seem to be any defined requirements for standard text, but as mentioned on <a href="https://www.w3.org/TR/WCAG20/#larger-scaledef" target="_blank">W3.org</a>, large text should be at least <span class="fancy">18pt = 1.5em = 24px</span> and <span class="fancy">14pt = 1.2em = 19px</span> for large bold text. Also from <a href="https://www.w3.org/QA/Tips/font-size" target="_blank">W3.org tips on font size</a>, it may be best to set normal text as <span class="fancy">12pt = 1em = 16px</span>.
        </p>

        <note :type="'tip'" :title="'tip'">
	        <p>
                All modern browsers will scale ems and maybe pixels as well, using <span class="fancy">Ctrl +</span> or <span class="fancy">Ctrl -</span>, but it is best recommended to not use pixels for font size.
	        </p>

	        <p>
                It seems like browsers may set the font size as 1em by default.
	        </p>
        </note>

        <note :type="'normal'">
            <h3>EMs:</h3>

	        <p>
                The base used is determined by the element's Parent. Since the "section" element has a font size of 24px, the base is 24px.
	        </p>

	        <p>
                Padding &amp; Margin use the current element's font size for the base. Using ems for padding or margins are for a more dynamic look to follow the changing font size.
	        </p>

            <section class="relative-sizes ems">
                <p class="em-1">font-size: 1em = base = 24px</p>
                <p class="em-1-5">font-size: 1.5em = 1.5(base) = 36px</p>
                <p class="em-2">font-size: 2em = 2(base) = 48px</p>
            </section>
            
            <h3 style="border-top: 2px solid rgba(0,0,0,.5); padding-top:20px;">REMs:</h3>
            
	        <p>
                The base font size is determined by the HTML Root. Even though the section element has a font size of 24px, the base font size is still 16px.
	        </p>

	        <p>
                Padding &amp; Margin use the HTML Root's font size for the base. Using rems for padding or margins are for a more consistent look no matter the font size.
	        </p>

            <section class="relative-sizes rems">
                <p class="rem-1">font-size: 1rem = base = 16px</p>
                <p class="rem-1-5">font-size: 1.5rem = 1.5(base) = 24px</p>
                <p class="rem-2">font-size: 2rem = 2(base) = 32px</p>
            </section>
        </note>

        <h3>Font Typeface:</h3>

        <p>
            All text should have a basic or easily-readable typeface (e.g. fonts that make the characters upper-case I, lower-case L, and number 1 all look similar should be avoided).
        </p>

        <note :type="'normal'">
	        <p style="font-family: Times New Roman;">
                Times New Roman: I, l, 1
	        </p>
	        <p style="font-family: Trebuchet MS;">
                Trebuchet MS: I, l, 1
	        </p>
	        <p>
                Using these two typefaces make the characters upper-case I, lower-case L, and number 1 all difficult to differentiate between one another.
	        </p>
        </note>

        <p>
            There are no defined requirements for a specific typeface to be used (due to difference of opions between experts). The recommended typefaces are those which are natively available in modern operating systems (e.g. Arial, Book Antiqua, Comic Sans MS, Georgia, Courier New, Tahoma, Times New Roman, Trebuchet MS, Verdana, etc.).
        </p>

        <note :type="'tip'" :title="'tip'">
            <p>
                Although the font families recommended are considered ADA compliant, not all text seem easily readable (in my opinion) and some make characters look too similar. The font families that I found that make text easy to read and distinguishable are <span class="fancy">Courier New</span>, <span class="fancy">Tahoma</span>, and <span class="fancy">Verdana</span>.
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
    export default class SectionFontStyles extends Vue {
        
    };
</script>

<style scoped>
section {
    font-size:24px;
}

.relative-sizes p {
    background-color: #009688;
    color: #fff;
    line-height: normal!important;
    margin: 1rem 1em 1em 1em!important;
}

.ems p{
    padding: 1em;
}

.em-1 {
    font-size: 1em!important;
}

.em-1-5 {
    font-size: 1.5em!important;
}

.em-2 {
    font-size: 2em!important;
}

.rems p{
    padding: 1rem;
}

.rem-1 {
    font-size: 1rem!important;
}

.rem-1-5 {
    font-size: 1.5rem!important;
}

.rem-2 {
    font-size: 2rem!important;
}
</style>
