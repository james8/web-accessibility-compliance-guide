<!--

-->

<template>
    <div id="section-color-contrast">
        <h2>MI-3. Background/Text Color Contrast</h2>

        <p>
            Make sure that any text is easily visible for those who are visually imparied. All text needs a well contrasting color compared to the color of its background.        
        </p>
        <p>
            According to the <a href="https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast.html" target="_blank">WCAG 2.0 guidelines</a>, the background/text contrast ratio must be the following ratios to be in compliance.
        </p>
        <table>
        <tbody><tr>
            <th class="no-border"></th>
            <th class="align-center">Any size text</th>
            <th class="align-center">Large text</th>
        </tr>
        <tr>
            <td class="align-right"><span class="fancy">Level AA</span></td>
            <td class="align-center">4.5:1</td>
            <td class="align-center">3:1</td>
        </tr>
        <tr>
            <td class="align-right"><span class="fancy">Level AAA</span></td>
            <td class="align-center">7:1</td>
            <td class="align-center">4.5:1</td>
        </tr>
        </tbody></table>

        <note :type="'tip'" :title="'tip'">
            <p>
                You can use the tota11y tool to check for text that are not in compliance. Start tota11y and select the Contrast test. The tota11y tool will often complain about text that is on top of a background image not being compliant. This is due to the fact that it can't tell what the background color is of the image and will just assume there is no background color (if none specified) to compare with the text color. If this happens just manually check the ratio by using the color of the background image.
            </p>
            <p>
                Also, a useful <a href="http://leaverou.github.io/contrast-ratio/" target="_blank">color contrast ratio calculator</a> tool to help easily identify if the background and text colors used are WCAG 2.0 compliant or not.
            </p>
        </note>

        <h3>Examples:</h3>

        <div class="color-contrast-ratios">
            <div class="one-seven-ratio ratio-box">Fails WCAG 2.0 compliance</div> 
            <div class="four-five-ratio ratio-box">Level AA compliant for any size text; Level AAA compliant for large text</div>
            <div class="twentyone-ratio ratio-box">Level AAA compliant for any size text</div>
        </div>
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
    export default class SectionColorContrast extends Vue {
        
    };
</script>

<style scoped>
    table {
        border-collapse: collapse;
        margin-top: 30px;
    }

    th.no-border {
        background-color: transparent;
        border: 0;
    }

    td:first-of-type, th {
        background-color: #e8eaf6;
    }

    td.align-right {
        text-align: right;
    }

    td.align-center, th.align-center {
        text-align: center;
    }

    td, th {
        border: 1px solid #000;
        padding: 5px 10px;
        width: 120px;
    }

    .color-contrast-ratios {
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-pack: justify;
        -ms-flex-pack: justify;
        justify-content: space-between;
    }

    .one-seven-ratio {
        background-color: #3f51b5;
        color: gray;
    }

    .four-five-ratio {
        background-color: #efefef;
        color: green;
    }

    .twentyone-ratio {
        background-color: #000;
        color: #fff;
    }

    .ratio-box {
        margin: 10px 0;
        padding: 20px 25px;
        width: 215px;
        -webkit-box-pack: center;
        -ms-flex-pack: center;
        justify-content: center;
        -webkit-box-align: center;
        -ms-flex-align: center;
        align-items: center;
    }

    @media (max-width: 800px) {
        .color-contrast-ratios {
            flex-direction: column;
        }
    }
</style>
