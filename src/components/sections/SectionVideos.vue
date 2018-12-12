<!--

-->

<template>
    <div id="section-videos">
        <h2>CI-4. Videos</h2>

        <p>
            Make sure that <span class="fancy">ALL</span> videos on a page have some form of <span class="fancy">closed captions</span> or <span class="fancy">text transcript</span> associated with them.  There needs to be some way for users who are hearing impaired to be able to know what is being said in the video.  An example of a video with closed captions can be viewed below.
        </p>

        <div class="videoWrapper">
            <iframe height="315" width="420" src="https://www.youtube.com/embed/watch?v=HtTyRajRuyY&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g"></iframe>
        </div>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from "vue-property-decorator";

    export default class SectionVideos extends Vue {
        
    };
</script>

<style scoped>
    .videoWrapper {
        display: flex;
        justify-content: center;
    }
</style>
