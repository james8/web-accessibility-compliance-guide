<!--

-->

<template>
    <div id="section-form-fields">
        <h2>CI-3. Form Fields</h2>

        <p>
            Make sure that all <span class="fancy">form fields</span> (i.e. input, textarea, etc.) have their respective <span class="fancy">labels</span>.  The purpose of having a label associated with a form field is to easily identify to a user what the data contained in the field represents.
        </p>
        <p>
            Make sure that all <span class="fancy">required</span> fields have the <span class="fancy">required</span> attribute associated with it.  You can add aesthetics or JavaScript to allow a sighted user to know if a field is required, but setting the required attribute is used to allow a Screen Reader to identify to a user that the field is required.
        </p>

        <note :type="'tip'" :title="'TIP'">
            <p>
                You can use the <span class="fancy">tota11y</span> tool to check for input fields that are not in compliance.  Start tota11y and select the <span class="fancy">Labels</span> test.
            </p>
        </note>

        <form-fields></form-fields>

        <note :type="'normal'">
            <p>
                As you can see, the first set of inputs (w/out labels) a user will not be able to know what the values <span class="fancy">red</span> and <span class="fancy">blue</span> represent.  With the second set, a user will know that <span class="fancy">red</span> represents the <span class="fancy">favorite color</span> and <span class="fancy">blue</span> represents the <span class="fancy">least favorite color</span>.
            </p>
        </note>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from "vue-property-decorator";

    import FormFields from "@/components/FormFields.vue";
    import Note from "@/components/Note.vue";

    @Component({
        components: {
            FormFields,
            Note
        }
    })
    export default class SectionFormFields extends Vue {
        
    };
</script>

<style scoped>

</style>

