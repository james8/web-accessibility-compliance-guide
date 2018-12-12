<!--

-->

<template>
    <div id="section-alt-text">
        <h2>CI-2. Image with Alternate Text</h2>

        <p>
            Make sure that <span class="fancy">ALL</span> images have an <span class="fancy">alternate text</span> associated with it.  An alternate text is used to describe to the user what the image is supposed to be if the image does not load.  Visually, this is only useful for sighted users, but for those who require a Screen Reader (such as NVDA Screen Reader) there is an additional benefit.  Screen Readers will read the alternate text attribute, but if there is none specified there will be nothing read.
        </p>

        <note :type="'tip'" :title="'TIP'">
            <p>
                You can use the <span class="fancy">tota11y</span> tool to check for any images on the page missing alternate text.  Start tota11y and select <span class="fancy">Image alt-text</span> test.
            </p>
        </note>

        <h3>Image w/out Alternate Text:</h3>
        <img src="https://com.somesite.www/example_img.png" />
        <note :type="'normal'">
            <p>
                Both sighted users and users needing assistance from a Screen Reader will not know what the image is supposed to be.
            </p>
        </note>

        <h3>Image w/ Alternate Text:</h3>
        <img src="https://com.somesite.www/example_img.png" alt="Example Image not found!!" />
        <note :type="'normal'">
            <p>
                A sighted user will see that the image is supposed to be some example image and a user needing assistance from a Screen Reader will be read <span class="fancy">example image not found</span>.
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
    export default class SectionAltText extends Vue {
        
    };
</script>

<style scoped>

</style>
