<!--

-->

<template>
    <div id="section-checkers">
        <h2>Web Accessibility Compliance Checkers</h2>

        <p>There are quite a few free web accessibility compliance checker tools that one can use.  The tools listed below are just some that are currently popular with others.</p>
        <ol>
            <li>
                <a href="http://khan.github.io/tota11y/" target="_blank">tota11y</a>
            </li>
            <li>
                <a href="https://chrome.google.com/webstore/detail/siteimprove-accessibility/efcfolpjihicnikpmhnmphjhhpiclljc" target="_blank">SiteImprove Accessibility Checker</a>
            </li>
            <li>
                <a href="https://wave.webaim.org/extension/" target="_blank">WAVE Web Accessibility Evaluation Tool</a>
            </li>
            <li>
                <a href="https://www.deque.com/axe/" target="_blank">aXe Browser Extension</a>
            </li>
        </ol>
        <note :type="'note'" :title="'note'">
            <p>All tools listed above only looks at a single page of a site (i.e. the current page being looked at will be evaluated).</p>
        </note>

        <h3>tota11y:</h3>
        <p>
            tota11y is a simple tool to help quickly check to see if your site is compliant.  To use, drag the <span class="fancy">tota11y</span> button below into your bookmarks bar.
            Navigate to your site and click on the bookmark to use.  Click on the <img alt="totally icon" src="./../../assets/tota11y.png" /> to use.
        </p>

        <a class="bookmarklet" href="javascript:(function(){var%20tota11y=document.createElement('SCRIPT');tota11y.type='text/javascript';tota11y.src='//khan.github.io/tota11y/tota11y/build/tota11y.min.js';document.getElementsByTagName('head')[0].appendChild(tota11y);})();" onclick="javascript:return false;">
            tota11y
        </a>

        <p>At the time this guide was created, there are currently seven different checks that can be done with the tota11y checker.</p>
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

        <h3>SiteImprove & WAVE Browser Extensions:</h3>
        <p>
            SiteImprove Accessibility Checker (currently only available for Chrome) & WAVE Web Accessibility Evaluation Tool (currently only available for Chrome & FireFox) are browser extensions that can be downloaded.
            These extensions do a more in depth evaluation on your site to provide you a list of errors & warnings where compliance is not met.
            Use of these browser extensions are best used by those who are a little more familiar with accessibility compliance since there are times where something may be marked as not compliant even though it is.
        </p>
        <p>
            To use, go to the <span class="fancy">Chrome Web Store</span> and download the desired browser extension (<span class="fancy">SiteImprove Accessibility Checker</span> or <span class="fancy">WAVE Web Accessibility Evaluation Tool</span>).
            Once installed, navigate to your site and run the extension.  Links to download the browser extensions are also listed above at the beginning of this section.
        </p>

        <h3>aXe Browser Extension:</h3>
        <p>
            aXe is another browser extension that can be downloaded (currently only available for Chrome & FireFox).  This extension also does a more in depth evaluation on your site to provide you a list of errors & warnings where compliance is not met.
            Use of this browser extension is best used by those who are developers since the results are not as user friendly as the SiteImprove & WAVE browser extension's results.
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
