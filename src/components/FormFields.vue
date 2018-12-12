<!--

-->

<template>
    <div id="form-fields">
        <h3>Examples:</h3>

        <div class="container">
            <input value="red" />
            <input value="blue" />
        </div>

        <hr />

        <div class="container">
            <div class="wrapper">
                <label for="input1">Favorite Color:</label>
                <input id="input1" value="red" />
            </div>

            <div class="wrapper">
                <label for="input2">Least Favorite Color:</label>
                <input id="input2" value="blue" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from "vue-property-decorator";
    
    @Component
    export default class FormFields extends Vue {
        
    };
</script>

<style scoped>
    #form-fields .container {
        display: flex;
        justify-content: space-around;
    }

    #form-fields .wrapper {
        display: flex;
        flex-direction: column;
    }

    #form-fields label {
        padding: 10px 0px;
    }
</style>

