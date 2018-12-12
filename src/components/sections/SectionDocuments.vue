<!--

-->

<template>
    <div id="section-documents">
        <h2>CI-5. Documents</h2>

        <p>
            Make sure that all <span class="fancy">document attachment(s)</span> are compliant for all users (this includes .pdf, .doc, .docx, etc.).  The requirements are similar to the requirements for web pages.  The main requirements are to make sure that text are not too small and has good color contrast, document has a good flow when read, and no ambiguous links (hyperlink text need to be meaningful), and images have an alternate text associated with them.
        </p>
        <p>
            More information can be obtained by referring to the <a href="https://www.w3.org/TR/WCAG-TECHS/pdf.html">PDF Techniques for WCAG 2.0</a> article.
        </p>

        <note :type="'normal'">
            <p>
                To add <span class="fancy">alternate text</span> to images in Microsoft Word, right click on the image and go to <span class="fancy">Format Image</span>.  PDFs can be set by using <span class="fancy">Adobe Acrobat 9 Pro</span>.
            </p>

            <h3>Adding alternate text via Microsoft Word 2010:</h3>
            <img id="ms-word-2010" src="./../../assets/AddingAltTextWord2010.png" alt="adding alternate text via Microsoft Word 2010" />
            
            <h3>Adding alternate text via Microsoft Word 2016:</h3>
            <img id="ms-word-2016" src="./../../assets/AddingAltTextWord2016.png" alt="adding alternate text via Microsoft Word 2016" />
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
    export default class SectionDocuments extends Vue {
        
    };
</script>

<style scoped>
    img {
        width: 100%;
    }

    #ms-word-2010 {
        max-width: 498px;
    }

    #ms-word-2016 {
        max-width: 282px;
    }
</style>

