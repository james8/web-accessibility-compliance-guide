<!--

-->

<template>
    <div id="section-documents">
        <h2>CI-5. Documents</h2>

        <p>
            Make sure that all <span class="fancy">document attachment(s)</span> are compliant for all users (this includes .pdf, .doc, .docx, etc.).
            The requirements are similar to the requirements for web pages.  The main requirements are to make sure that text are not too small and has good
            color contrast, document has a good flow when read, and no ambiguous links (hyperlink text need to be meaningful), and images have an alternate text associated with them.
        </p>

        <h3>Adding Alternative Text:</h3>
        <ul>
            <li>
                <h4>Microsoft Word:</h4>
                <p>
                    To add <span class="fancy">alternative text</span> to images in Microsoft Word, right click on the image and go to <span class="fancy">Format Image</span>.
                    Below are images of the properties window for Microsoft Word 2010 & 2016, respectively.
                </p>
                <img id="ms-word-2010" src="./../../assets/AddingAltTextWord2010.png" alt="adding alternate text via Microsoft Word 2010" />
                <br />
                <img id="ms-word-2016" src="./../../assets/AddingAltTextWord2016.png" alt="adding alternate text via Microsoft Word 2016" />
            </li>
            <li>
                <h4>PDF:</h4>
                <p>To add <span class="fancy">alternative text</span> to images in PDFs, refer to <a href="https://www.w3.org/TR/WCAG-TECHS/pdf.html#PDF1" target="_blank">PDF1: Applying text alternatives to images with the Alt entry in PDF documents</a>.</p>
            </li>
        </ul>

        <h3>Optical Character Recognition (OCR) on PDFs</h3>
        <p>
            To perform <span class="fancy">Optical Character Recognition (OCR)</span> on PDFs, refer to
            <a href="https://www.w3.org/TR/WCAG-TECHS/pdf.html#PDF7" target="_blank">Performing OCR on a scanned PDF document</a> or
            <a href="https://acrobat.adobe.com/us/en/acrobat/how-to/ocr-software-convert-pdf-to-text.html" target="_blank">Use OCR software in Acrobat</a>.
        </p>
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

