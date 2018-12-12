<!--

-->

<template>
    <div id="section-helpful-resources">
        <h2>Helpful Resources</h2>
        <ol>
            <li>
                <a href="https://www.w3.org/TR/UNDERSTANDING-WCAG20/Overview.html" target="_blank">WCAG 2.0 ADA Compliance Guidelines</a> are a set of guidelines and best practices put together by accessibility experts to explain what accessibility means and how to make a site compliant.
            </li>
            <li>
                <a href="https://www.w3.org/TR/wai-aria-practices-1.1/" target="_blank">WAI-ARIA documentation</a> in section <span class="fancy">3. Design Patterns and Widgets</span> for best practices and examples for making elements compliant.
            </li>
            <li>
                <a href="https://webaim.org/standards/wcag/checklist" target="_blank">WebAIM's WCAG 2.0 Checklist</a> is a checklist that can be used to help determine if the WCAG guidelines are being followed.
            </li>
            <li>
                <a href="https://a11yproject.com/" target="_blank">The A11y Project</a> is another helpful resource for how-tos and tips maintained by a community of people.
            </li>
            <li>
                <a href="https://www.youtube.com/watch?v=HtTyRajRuyY&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g" target="_blank">A11ycast</a> is a set of YouTube videos by Google that helps explain accessibility issues and how to go about fixing some of them.
            </li>
            <li>
                <a href="https://www.udacity.com/course/web-accessibility--ud891" target="_blank">Accessibility Fundementals on Udacity</a> is a set of lessons that helps to explain accessibility issues and how to go about fixing some of them.
            </li>
        </ol>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from "vue-property-decorator";

    @Component
    export default class SectionHelpfulResources extends Vue {
    }
</script>

<style scoped>
li {
    margin: 20px 0;
}
</style>
