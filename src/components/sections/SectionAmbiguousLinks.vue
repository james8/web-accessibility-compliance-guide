<!--

-->

<template>
    <div id="section-ambiguous-links">
        <h2>MI-5. Ambiguous Links</h2>

        <p>
            Make sure that there are no ambiguous link text (e.g. multiple "read more", "learn more", "here", "view", etc.) on a page. Although giving links ambiguous text may be easily read (and aestheticly pleasing) by a sighted user, it may be difficult for a user needing assistance from a Screen Reader. A Screen Reader will read whatever text was provided for the link to the user. So if multiple links say the same thing, it may confuse the user as to where the link will take them.
        </p>

        <note :type="'tip'" :title="'tip'">
            <p>
                If trying to just make link ADA compliant, it may be easiest to just make the link text more descriptive.
            </p>
            <p>
                For the following examples and the links on your own site, the <span class="fancy">tota11y</span> tool or a Screen Reader can be used to see what is read from a link.
            </p>
        </note>

        <h3>Ambiguous Links:</h3>

        <div class="link-sections">
            <div>
                <h4>Dogs</h4>
                <a href="/#ambiguous-links">Learn More</a>
            </div>
            <div>
                <h4>Cats</h4>
                <a href="/#ambiguous-links">Learn More</a>
            </div>
            <div>
                <h4>Birds</h4>
                <a href="/#ambiguous-links">Learn More</a>
            </div>
        </div>

        <note :type="'normal'" >
            <p>
                A Screen Reader will read each link as <span class="fancy">"learn more"</span>. A user using a Screen Reader may be trying to learn more about "cats", but mistakenly select the link for "dogs" since they are read identically.
            </p>
        </note>

        <h3>Non-Ambiguous Links:</h3>

        <div class="link-sections">
            <div>
                <h4>Dogs</h4>
                <a href="/#ambiguous-links">Learn More about Dogs</a>
            </div>
            <div>
                <h4>Cats</h4>
                <a href="/#ambiguous-links">Learn More about Cats</a>
            </div>
            <div>
                <h4>Birds</h4>
                <a href="/#ambiguous-links">Learn More about Birds</a>
            </div>
        </div>

        <note :type="'normal'" >
            <p>
                A user using a Screen Reader can easily distinguish which link will do what.
            </p>
        </note>        

        <note :type="'tip'" :title="'tip'" >
            <p>
                You can leave the ambiguous link text as is and add additional text (but hidden) to be read from the Screen Reader. Alternatively, you can add either the <span class="fancy">aria-label</span> or <span class="fancy">aria-labelledby</span> attribute.
            </p>
            <p>
                To add additional hidden text, do the following:
            </p>
            <ol>
                <li>In the <span class="fancy">anchor tag</span> add a <span class="fancy">span element</span> with additional text.</li>
                <li>Add the CSS styles <span class="fancy">"height: 1px; width: 1px; overflow: hidden; display: block;"</span> to the span element.</li>
            </ol>
        </note>

        <div class="link-sections">
            <div>
                <h4>Dogs</h4>
                <a href="/#ambiguous-links">Learn More<span>about dogs</span></a>
            </div>
            <div>
                <h4>Cats</h4>
                <a href="/#ambiguous-links">Learn More<span>about cats</span></a>
            </div>
            <div>
                <h4>Birds</h4>
                <a href="/#ambiguous-links">Learn More<span>about birds</span></a>
            </div>
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
    export default class SectionAmbiguousLinks extends Vue {
        
    };
</script>

<style scoped>
.link-sections{
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-pack: space-evenly;
    -ms-flex-pack: space-evenly;
    justify-content: space-evenly;
}

.link-sections div {
    border: 1px solid #363636;
    padding: 0 15px 15px 15px;
    width: 180px;
}

.link-sections span {
    height: 1px;
    overflow: hidden;
    width: 1px;
    display: block;
}
</style>
