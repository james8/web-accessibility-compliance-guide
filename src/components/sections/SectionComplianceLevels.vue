<!--

-->

<template>
    <div id="section-compliance-levels">
        <h2>Compliance Levels</h2>
        <p>
            According to the WCAG 2.0 compliance guidelines, there are three levels of compliance that can be followed (<span class="fancy">Level A</span>, <span class="fancy">Level AA</span>, and <span class="fancy">Level AAA</span>).  The higher the compliance level, the more restrictive it becomes on how the web page is designed and presented.  As a rule-of-thumb when designing your web page, you should always try to achieve a compliance Level AAA for all criteria.  Since Level AAA is the most restrictive and may be hard to satisfy due to design constraints, its sometimes okay to not meet a AAA compliance for everything.  If the design restrainsts are too much, it's okay to make certain aspects comply with only a Level AA.
        </p>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from "vue-property-decorator";

    @Component
    export default class SectionComplianceLevels extends Vue {
    }
</script>

<style scoped>

</style>
