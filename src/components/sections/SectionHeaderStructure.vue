<!--

-->

<template>
    <div id="section-header-structure">
        <h2>MI-6. Header Structure</h2>

        <p>
            Make sure that the proper <span class="fancy">header</span> structuring is being used on all pages. The proper header structuring is to have headers placed in accordance to importance and not skipping over any. For example, if you are trying to add a header 2 tag, you must have a header 1 tag declared somewhere before the header 2. Proper header structure is used for those needing assistance from a Screen Reader, as headers are used to allow users to easily skip around the page without having to go through the entire content. If the proper structure is not used the Screen Reader may have difficulty navigating correctly.  
        </p>

        <note :type="'tip'" :title="'tip'">
            <p>
                Don't use header tags for aesthetic purposes (e.g. using headers as a label that's already styled). Instead, create a custom tag and style it with CSS. Headers should only be used to indicate text is the beginning of a section.
            </p>
            <p>
                You can use the <span class="fancy">tota11y</span> tool to check if the current page is using the proper header structure. Start tota11y and select the <span class="fancy">Headings</span> test.
            </p>
            <p>
                <span class="fancy">ARIA Landmarks</span> is another way for Screen Readers to jump between content quickly. Read more about <a href="https://accessibility.oit.ncsu.edu/it-accessibility-at-nc-state/developers/accessibility-handbook/aria-landmarks/" target="_blank">ARIA landmarks</a>
            </p>
        </note>

        <h3>Incorrect Header Structure:</h3>
        <div class="header-group">
            <h2>H2: Missing an H1 tag</h2>
            <h3>H3: Some content</h3>
            <h3>H3: More content</h3>
            <h2>H2: Still missing an H1 tag</h2>
            <h4>H4: Missing H3 tag</h4>
        </div>        

        <note :type="'normal'" >
            <p>
                In the example above, there is no starting <span class="fancy">header 1</span> tag and there is no <span class="fancy">header 3</span> tag between the header 2 &amp; header 4 tags. This is not proper structuring for headers and may cause problems for Screen Readers.
            </p>
        </note>        

        <h3>Correct Header Structure:</h3>
        <div class="header-group">
            <h1>H1: Section Title</h1>
            <h2>H2: Subsection Title</h2>
            <h3>H3: Some content</h3>
            <h3>H3: More content</h3>
            <h2>H2: Subsection Title 2</h2>
            <h3>H3: Even more content</h3>
            <h4>H4: Lots of content</h4>
        </div>           

        <note :type="'normal'" >
            <p>
                The example above has proper structuring for headers as each header has an appropriate parent header declared.
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
    export default class SectionSkipNavigation extends Vue {
        
    };
</script>

<style scoped>
.header-group {
    padding-left: 30px!important;
}

.header-group h1 {
    margin: 1em 0!important;
}

.header-group h2 {
    letter-spacing: .01px;
    margin: 0px 0px 10px 30px;
    color: #034565;
    font-size: 24px;
    line-height: 24px;
}

.header-group h3 {
    margin-top: 18.72px!important;
    margin-bottom: 18.72px!important;
    margin-left: 60px!important;
    text-decoration: none;
}

.header-group h4 {
    margin-left: 90px!important;
}
</style>
