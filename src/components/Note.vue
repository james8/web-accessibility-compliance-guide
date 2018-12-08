<!--
    @Prop type: ['normal', 'warning', 'tip']        -> Note type
    @Prop title?: string                            -> Title to be used (optional)
-->

<template>
    <div id="note" v-bind:class="`${ type }Note`">
        <p class="noteTitle">{{ title }}:</p>
        <slot></slot>
    </div>
</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    @Component
    export default class Note extends Vue {
        @Prop({ type: String }) type!: string;
        @Prop({ type: String }) title!: string;

        created(): void {
            if ((this.type !== 'normal') && (this.type !== 'warning') && (this.type !== 'tip')) this.type = 'normal';
        }
    }
</script>

<style scoped>
    #note {
        margin: 20px auto;
        max-width: 1200px;
        padding: 10px 20px;
    }

    .normalNote {
        background-color: #e8eaf6;
        border-left: 6px solid #3f51b5;
    }

    .warningNote {
        background-color: #fee;
        border-left: 6px solid #d80707;
    }

    .tipNote {
        background-color: #ffecb3;
        border-left: 6px solid #ffc107;
    }

    .noteTitle {
        font-weight: bold;
        text-decoration: underline;
        text-transform: uppercase;
    }
</style>

