<template>
    <div id="app">
        <header>
            <h1>{{ title }}</h1>
            <p>
                The purpose of this guide is to provide assistance to help you determine if there are any incompliances of your own custom site in accordance with the Americans with Disabilities Act (ADA).  The <a href="https://www.w3.org/TR/UNDERSTANDING-WCAG20/Overview.html" target="_blank">WCAG 2.0 ADA compliance guidelines</a> are the standards used to explain how to make a site ADA compliant.  As a state agency, all Hawaii Department of Education public facing websites needs to be compliant to allow any user the ability to access all the information of a given site.  The WCAG 2.1 ADA compliance guidelines (which are an extension of requirements to WCAG 2.0) will be released sometime in the near future, so additional fixes may need to be done to comply with these new requirements.
            </p>
            <p>
                For additional help, please refer to the <span>Helpful Resources</span> section below.
            </p>

            <br/><br/>
            <note :type="'warning'" :title="'disclaimer'">
                <p>
                    This guide may have some inconsistencies due to the author's interpretations of the WCAG compliance guidelines.  For the most accurate check, please refer to the <a href="https://www.w3.org/TR/UNDERSTANDING-WCAG20/Overview.html" target="_blank">WCAG 2.0 ADA compliance guidelines</a> which should be followed to be compliant.
                </p>
            </note>
        </header>

        <parallax :image="require('@/assets/jellyfish.jpg')"></parallax>

        <section-table-of-contents :data="tocLinks" class="section"></section-table-of-contents>

        <div v-for="section in sections" :key="section.id" class="section">
            <div :is="section.tag" :key="section.component"></div>
        </div>

        <div id="section-critical-issues" class="section">
            <h1>Critical Issues (CIs)</h1>
            <p>
                Critical issues <span class="fancy">NEED</span> to be addressed to make sure everyone can access all content on the page.  These issues, if not addressed, are those that would cause a user (under certain circumstances) to not be able to access the same content or information which another user would have no problem accessing.
            </p>
        </div>

        <div v-for="ciSection in ciSections" :key="ciSection.id" class="section">
            <div :is="ciSection.tag" :key="ciSection.component"></div>
        </div>

        <section-resources class="section"></section-resources>

        <footer>
            <p>Last Modified: 12/2018</p>
        </footer>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from 'vue-property-decorator';

    import Note from "@/components/Note.vue";
    import Parallax from "@/components/Parallax.vue";
    import SectionAltText from "@/components/sections/SectionAltText.vue";
    import SectionCheckers from "@/components/sections/SectionCheckers.vue";
    import SectionComplianceLevels from "@/components/sections/SectionComplianceLevels.vue";
    import SectionDocuments from "@/components/sections/SectionDocuments.vue";
    import SectionFormFields from "@/components/sections/SectionFormFields.vue";
    import SectionNavigation from "@/components/sections/SectionNavigation.vue";
    import SectionResources from "@/components/sections/SectionResources.vue";
    import SectionScreenReaders from "@/components/sections/SectionScreenReaders.vue";
    import SectionTableOfContents from "@/components/sections/SectionTableOfContents.vue";
    import SectionVideos from "@/components/sections/SectionVideos.vue";

    interface ISection {
        label: string,      // link's label
        level: number,      // 0: link (w/ padded top); 1: link; 2: sub-link
        component: string,	// Component's name
        tag: string         // Component's tag
    };

    @Component({
        components: {
            Note,
            Parallax,
            SectionAltText,
            SectionCheckers,
            SectionComplianceLevels,
            SectionDocuments,
            SectionFormFields,
            SectionNavigation,
            SectionResources,
            SectionScreenReaders,
            SectionTableOfContents,
            SectionVideos
        }
    })
    export default class App extends Vue {
        title: string = "";
        tocLinks: Array<ISection> = [];
        sections: Array<ISection> = [];
        ciSections: Array<ISection> = [];

        created(): void {
            this.title = "Web Accessibility Compliance Guide";

            this.sections = [
                {
                    label: 'Compliance Levels',
                    level: 1,
                    component: 'SectionComplianceLevels',
                    tag: 'section-compliance-levels'
                },
                {
                    label: 'Web Accessibility Compliance Checkers',
                    level: 1,
                    component: 'SectionCheckers',
                    tag: 'section-checkers'
                },
                {
                    label: 'Screen Readers',
                    level: 1,
                    component: 'SectionScreenReaders',
                    tag: 'section-screen-readers'
                }
            ];

            const ci: ISection = {
                label: 'Critical Issues',
                level: 0,
                component: '',
                tag: 'section-critical-issues'
            };
            this.ciSections = [
                {
                    label: '1. Navigation',
                    level: 2,
                    component: 'SectionNavigation',
                    tag: 'section-navigation'
                },
                {
                    label: '2. Image with Alternate Text',
                    level: 2,
                    component: 'SectionAltText',
                    tag: 'section-alt-text'
                },
                {
                    label: '3. Form Fields',
                    level: 2,
                    component: 'SectionFormFields',
                    tag: 'section-form-fields'
                },
                {
                    label: '4. Videos',
                    level: 2,
                    component: 'SectionVideos',
                    tag: 'section-videos'
                },
                {
                    label: '5. Documents',
                    level: 2,
                    component: 'SectionDocuments',
                    tag: 'section-documents'
                }
            ];

            const r: ISection = {
                label: 'Helpful Resources',
                level: 0,
                component: 'SectionResources',
                tag: 'section-resources'
            };

            this.tocLinks = [...this.sections, ci, ...this.ciSections, r];
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    header, .section {
        margin: auto;
        max-width: 1200px;
        padding: 20px 50px;
        text-align: justify;
    }

    .section {
        border-top: 4px double #bdbdbd;
    }

    #section-table-of-contents {
        border-top: none;
    }

    header h1 {
        text-align: center;
    }

    .section h2 {
        text-align: left;
    }
        
    .section h3 {
        padding-top: 20px;
        text-decoration: underline;
    }

    .fancy {
        font-style: italic;
        font-weight: bold;
    }

    footer {
        border-top: 4px double #bdbdbd;
    }
</style>
