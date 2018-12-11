<!--

-->

<template>
    <div id="navigation-nc">
        <button type="button" id="focus-btn" @blur="FocusHere(0);" @focus="FocusHere(1);">{{ focusBtnText }}</button>

        <nav>
            <ul class="mainMenu">
                <li v-for="(menu, index) in menus" :key="menu.index" @mouseleave="ShowSubmenu(0, index);" @mouseenter="ShowSubmenu(1, index);" tabindex="0">
                    <span>{{ menu.name }}</span>
                    <ul :id="`subMenu${ index }`" class="subMenu hidden">
                        <li v-for="submenu in menu.submenus" :key="submenu.index">
                            <a :href="`#${ link }`">{{ submenu.name }}</a>
                        </li>
                    </ul>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    interface IMenu {
        name: string;
        submenus?: Array<IMenu>
    }

    @Component
    export default class NavigationNc extends Vue {
        @Prop({ type: String, required: true }) link!: string;

        focusBtnText: string = "";
        menus: Array<IMenu> = [];

        created(): void {
            this.focusBtnText = "Focus Here";
            this.menus = [
                {
                    name: "Menu 1",
                    submenus: [
                        { name: "Submenu 1-1" }
                    ]
                },
                {
                    name: "Menu 2",
                    submenus: [
                        { name: "Submenu 2-1" },
                        { name: "Submenu 2-2" }
                    ]
                },
                {
                    name: "Menu 3",
                    submenus: [
                        { name: "Submenu 3-1" },
                        { name: "Submenu 3-2" },
                        { name: "Submenu 3-3" }
                    ]
                }
            ];
        }

        FocusHere(type: boolean): void {
            if (!type) this.focusBtnText = "Focus Here";
            else {
                this.focusBtnText = "Focused";
                (document.querySelector('#navigation-nc #focus-btn') as HTMLElement).focus();
            }
        }

        ShowSubmenu(type: boolean, index: number): void {
            const elem: Element = document.getElementById(`subMenu${ index }`) as HTMLElement;
            if (!type) elem.classList.add('hidden');
            else elem.classList.remove('hidden');
        }
    };
</script>

<style scoped>
    #navigation-nc {
        margin: 16px 0px;
        display: flex;
    }

    #focus-btn {
        background-color: #f7f7f7;
        border: 1px solid #b9b9b9;
        cursor: pointer;
        height: 38px;
        width: 125px;
    }

    #focus-btn:hover {
        background-color: #e9e9e9;
        border-color: #9f9f9f;
    }

    nav {
        padding-left: 40px;
    }

    ul {
        box-shadow: 5px 5px 5px #878787;
        list-style-type: none;
        margin: 0 0 0 10px;
        padding: 0;
        display: flex;
    }

    .mainMenu li {
        background-color: #546e7a;
        color: #fff;
        cursor: pointer;
        height: 38px;
        width: 150px;
        position: relative;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .mainMenu li:hover {
        background-color: #1565c0;
    }

    .subMenu {
        position: absolute;
        top: 38px;
        right: 0px;
        flex-direction: column;
    }

    .subMenu li {
        background-color: #fff;
    }

    .subMenu li:hover {
        background-color: #64b5f6;
    }

    .subMenu a {
        color: #000;
        text-decoration: none;
    }

    .hidden {
        display: none;
    }
</style>
