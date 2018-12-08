<!--

-->

<template>
    <div id="section-table-of-contents">
        <h2>Table of Contents</h2>
        <div class="tocLinks">
            <a v-bind:href="`#${ link.tag }`" v-for="link in data" :key="link.id" v-bind:class="`level${ link.level }`">{{ link.label }}</a>
        </div>
    </div>
</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    @Component
    export default class SectionTableOfContents extends Vue {
        @Prop({ type: Array, required: true }) data!: Array<Object>
    };
</script>

<style scoped>
    .tocLinks {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }

    .tocLinks {
        line-height: 30px;
        text-decoration: underline;
    }

    .tocLinks a:hover {
        color: purple;
    }

    .level0 {
        padding-top: 10px;
    }

    .level2 {
        padding-left: 25px;
    }
</style>
