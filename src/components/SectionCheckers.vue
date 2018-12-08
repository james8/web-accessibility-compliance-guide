<!--

-->

<template>
    <div id="section-checkers">
        <h2>Web Accessibility Compliance Checkers</h2>

        <p>
            <span class="fancy">tota11y</span> is a useful free web accessibility compliance checker tool to use when making sure your site is compliant.  To use, drag the <span class="fancy">tota11y</span> button below into your bookmarks bar.  Navigate to your site and click on the bookmark to use.  Click on the <img alt="totally icon" src="./../assets/tota11y.png" /> to use.
        </p>

        <a class="bookmarklet" href="javascript:(function(){var%20tota11y=document.createElement('SCRIPT');tota11y.type='text/javascript';tota11y.src='//khan.github.io/tota11y/tota11y/build/tota11y.min.js';document.getElementsByTagName('head')[0].appendChild(tota11y);})();" onclick="javascript:return false;">
            tota11y
        </a>

        <p>At the time this site was created, there are currently seven different checks that can be done with the tota11y checker.</p>
        <ol>
            <li>
                <span class="fancy">Headings</span>: Check for correct heading structuring.
            </li>
            <li>
                <span class="fancy">Contrast</span>: Check for elements with low color contrast between text and background.
            </li>
            <li>
                <span class="fancy">Link text</span>: Check for any links that have ambiguous checks.
            </li>
            <li>
                <span class="fancy">Labels</span>: Check for any input fields missing their respective labels.
            </li>
            <li>
                <span class="fancy">Image alt-text</span>: Check for any images that are missing their respective alternate text.
            </li>
            <li>
                <span class="fancy">Landmarks</span>: Check for all ARIA landmarks.
            </li>
            <li>
                <span class="fancy">Screen Reader Wand</span>: Check how a <span class="fancy">Screen Reader</span> would read a specific element (may not be entirely what a Screen Reader would read, it's best to use an actual reader to check what is being read).
            </li>
        </ol>

        <note :type="'warning'" :title="'warning'">
            <p>
                The <span class="fancy">tota11y</span> checker does not work on every site.  This is due to the way certain sites are set up (i.e. using a site builder like Wix or Weebly) which may have some built-in features that cause the checker to not work properly.
            </p>
        </note>

        <p>
            Another useful free web accessibility compliance checker tool to use is the <span class="fancy">WAVE web accessibility evaluation tool</span>, which is a Chrome extension that can be downloaded.  The WAVE evaluation tool contains a bit more information which may make it more complicated to figure out what is not in compliance and why.  To use, go to the <span class="fancy">Chrome Web Store</span> and download the <span class="fancy">WAVE web accessibility evaluation tool</span> extension.  Once installed, navigate to your site and run the extension.
        </p>
        <img alt="wave web accessibility evaluation tool logo" src="./../assets/WAVETool.png" />
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
    export default class SectionCheckers extends Vue {
    };
</script>

<style scoped>
    .bookmarklet {
        border-radius: 5px;
        border: 3px solid #333;
        color: #333;
        font-weight: 700;
        margin: 10px 0;
        padding: 10px 25px;
        text-decoration: none;
        display: inline-block;
    }

    li {
        padding-top: 10px;
    }
</style>
