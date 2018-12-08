<!--
    @Prop image: string      -> Image to be used (pass using require() to have image loaded)
-->

<template>
    <div id="parallax"></div>
</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    @Component
    export default class Parallax extends Vue {
        @Prop({ type: String, required: true }) image!: string;

        created(): void {
            setTimeout(() => {
                const elem: Element = document.getElementById('parallax') as Element;
                elem.setAttribute('style', `background-image: url(${ this.image })`);
            }, 50);
        }
    }
</script>

<style scoped>
    #parallax {
        background-attachment: fixed;
        background-color: #d8d8d8;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        height: 550px;
    }
</style>
