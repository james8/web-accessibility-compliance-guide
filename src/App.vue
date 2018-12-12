<template>
    <div id="app">
        <div class="skip-navigation" tabindex="0">SKIP TO MAIN CONTENT</div>

        <div id="back-to-top"  v-scroll-class:visible=950>
            <span>Back</span>
            <span>to Top</span>
        </div>
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

        

        <div id="section-moderate-issues" class="section">
            <h1>Moderate Issues (MIs)</h1>
            <p>
                Moderate issues do not need to, but <span class="fancy">SHOULD</span> be addressed to make viewing content on the page easy for everyone. These issues, if not addressed, could make it difficult for some users to view certain content but will still be able to access all content or information which another user would have no problem (unless the issue is so severe, like text color being the same color as the background which makes it impossible to see by everyone). 
            </p>
        </div>

        <div v-for="miSection in miSections" :key="miSection.id" class="section">
            <div :is="miSection.tag" :key="miSection.component"></div>
        </div>

        <div v-for="endSection in endSections" :key="endSection.id" class="section">
            <div :is="endSection.tag" :key="endSection.component"></div>
        </div>

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
    import SectionFocusableElements from "@/components/sections/SectionFocusableElements.vue";
    import SectionOffScreenContent from "@/components/sections/SectionOffScreenContent.vue";
    import SectionColorContrast from "@/components/sections/SectionColorContrast.vue";
    import SectionSkipNavigation from "@/components/sections/SectionSkipNavigation.vue";
    import SectionAmbiguousLinks from "@/components/sections/SectionAmbiguousLinks.vue";
    import SectionHeaderStructure from "@/components/sections/SectionHeaderStructure.vue";
    import SectionFontStyles from "@/components/sections/SectionFontStyles.vue";
    import SectionMobileView from "@/components/sections/SectionMobileView.vue";
    import SectionHelpfulResources from "@/components/sections/SectionHelpfulResources.vue";
    import VueScrollClass from '@/../node_modules/vue-scroll-class';
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
            SectionFocusableElements,
            SectionOffScreenContent,
            SectionColorContrast,
            SectionSkipNavigation,
            SectionAmbiguousLinks,
            SectionHeaderStructure,
            SectionFontStyles,
            SectionMobileView,
            SectionHelpfulResources,
            SectionVideos
        },
        directives: {
            'scroll-class': VueScrollClass
        }
    })
    export default class App extends Vue {
        title: string = "";
        tocLinks: Array<ISection> = [];
        sections: Array<ISection> = [];
        ciSections: Array<ISection> = [];
        miSections: Array<ISection> = [];
        endSections: Array<ISection> = [];

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

            const mi: ISection = {
                label: 'Moderate Issues',
                level: 0,
                component: '',
                tag: 'section-moderate-issues'
            };
            this.miSections = [
                {
                    label: '1. Focusable Elements',
                    level: 2,
                    component: 'SectionFocusableElements',
                    tag: 'section-focusable-elements'
                },
                {
                    label: '2. Off-Screen Content',
                    level: 2,
                    component: 'SectionOffScreenContent',
                    tag: 'section-off-screen-content'
                },
                {
                    label: '3. Background/Text Color Contrast',
                    level: 2,
                    component: 'SectionColorContrast',
                    tag: 'section-color-contrast'
                },
                {
                    label: '4. Skip Navigation',
                    level: 2,
                    component: 'SectionSkipNavigation',
                    tag: 'section-skip-navigation'
                },
                {
                    label: '5. Ambiguous Links',
                    level: 2,
                    component: 'SectionAmbiguousLinks',
                    tag: 'section-ambiguous-links'
                },
                {
                    label: '6. Header Structure',
                    level: 2,
                    component: 'SectionHeaderStructure',
                    tag: 'section-header-structure'
                },
                {
                    label: '7. Font Styles',
                    level: 2,
                    component: 'SectionFontStyles',
                    tag: 'section-font-styles'
                },
                {
                    label: '8. Mobile View',
                    level: 2,
                    component: 'SectionMobileView',
                    tag: 'section-mobile-view'
                }                
            ];
            
            this.endSections = [
                {
                    label: 'Helpful Resources',
                    level: 0,
                    component: 'SectionHelpfulResources',
                    tag: 'section-helpful-resources'
                }
            ];

            this.tocLinks = this.sections;
            this.tocLinks = [...this.tocLinks, ci, ...this.ciSections, mi, ...this.miSections, ...this.endSections];
            // console.table(this.tocLinks);
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
        font-family: Verdana, Geneva, Tahoma, sans-serif;
        font-size: 12pt;
    }

    h1 {
        font-size: 2em;
        margin: 1em 0px;
    }

    h2 {
        font-size: 1.5em;
        font-weight: 700;
        margin: 19.92px 0px;
    }

    h3 {
        font-size: 1.17em;
        font-weight: 700;
        margin: 45px 0px 15px 0px;
    }

    h4 {
        font-size: 1.33em;
        font-weight: 700;
        margin: 21.28px 0px;
    }

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

    h3{
        text-decoration: underline;
        margin-top:45px;
    }

    .skip-navigation {
        color: blue;
        cursor: pointer;
        height: 1px;
        overflow: hidden;
        text-decoration: underline;
        width: 1px;
        position: fixed;
        top: 0;
        left: 0;
    }

    #back-to-top {
        background: #c8e6c9;
        border: 4px solid #4caf50;
        box-sizing: initial;
        border-radius: 5px;
        color: #000!important;
        cursor: pointer;
        height: 37px;
        opacity: 0;
        padding: 5px;
        text-decoration: none!important;
        width: 65px;
        position: fixed;
        right: 10px;
        bottom: 10px;
        z-index: -10;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
        -ms-flex-direction: column;
        flex-direction: column;
        -webkit-box-align: center;
        -ms-flex-align: center;
        align-items: center;
        transition: opacity .5s ease;
    }

    #back-to-top.visible {
        opacity: 1;
        z-index: 10;
        transition: opacity .5s ease;
    }

    #back-to-top:hover {
        background-color:#ffe0b2;
        border-color:#ff9800;
    }

    footer {
        border-top: 4px double #bdbdbd;
    }
</style>

