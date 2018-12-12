<!--

-->

<template>
    <div id="navigation">
        <button type="button" id="focus-btn" @blur="FocusHere($event);" @focus="FocusHere($event);">{{ focusBtnText }}</button>

        <nav role="application">
            <ul class="mainMenu" role="menu">
                <li v-for="(menu, index) in menus" :key="index" role="menuitem" aria-haspopup="true" :tabindex="(focusedMenu === index) ? '0' : '-1'"
                    @mouseleave="ShowSubmenu($event, 0);" @mouseenter="ShowSubmenu($event, 1);"
                    @keydown.arrow-left="MoveMenu($event);" @keydown.arrow-right="MoveMenu($event);"
                    @keydown.escape="KBShowSubmenu($event, 0);" @keydown.enter="KBShowSubmenu($event, 1);"
                    @keydown.arrow-up="MoveSubmenu($event);" @keydown.arrow-down="MoveSubmenu($event);">
                    <span>{{ menu.name }}</span>
                    <ul :id="`subMenu${ index }`" class="subMenu hidden" role="menu">
                        <li v-for="submenu in menu.submenus" :key="submenu.index" role="none">
                            <a :href="`#${ link }`" class="subMenuLink" tabindex="-1" role="menuitem">{{ submenu.name }}</a>
                        </li>
                    </ul>
                </li>
            </ul>
        </nav>

        <button type="button" id="reset-btn" @focus="ResetMenu();">Reset Menu</button>
    </div>
</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    interface IMenu {
        name: string;
        submenus?: Array<IMenu>
    }

    @Component
    export default class Navigation extends Vue {
        @Prop({ type: String, required: true }) link!: string;

        focusBtnText: string = "";
        menus: Array<IMenu> = [];
        menuItems: any = [];
        submenuItems: any = [];
        focusedMenu: number = 0;
        focusedSubmenu: number = 0;

        created(): void {
            this.focusBtnText = "Focus Here";
            this.menus = [
                {
                    name: "Menu 1",
                    submenus: [
                        { name: "Submenu 1-1" },
                        { name: "Submenu 1-2" },
                        { name: "Submenu 1-3" }
                    ]
                },
                {
                    name: "Menu 2",
                    submenus: [
                        { name: "Submenu 2-1" },
                        { name: "Submenu 2-2" }
                    ]
                }
            ];

            setTimeout(() => {
                this.menuItems = document.querySelectorAll('#navigation .mainMenu > li') as NodeListOf<HTMLElement>
                this.menuItems.forEach((menuItem: HTMLElement, i: number) => {
                    menuItem.tabIndex = ((i !== 0) ? -1 : 0);
                });
            }, 50);
        }

        FocusHere(event: Event): void {
            const elem: HTMLElement = event.target as HTMLElement;
            if (elem.innerHTML === 'Focused') this.focusBtnText = "Focus Here";
            else {
                this.focusBtnText = "Focused";
                elem.focus();
            }
        }

        ShowSubmenu(event: Event, type: boolean): void {
            const elem: HTMLElement = (event.target as HTMLElement).querySelector('.subMenu') as HTMLElement;
            if (!type) elem.classList.add('hidden');
            else elem.classList.remove('hidden');
        }

        KBShowSubmenu(event: KeyboardEvent, type: boolean): void {
            // close submenu
            if (!type && (event.target as HTMLElement).classList.contains('subMenuLink')) {
                // close submenus
                const elems: NodeListOf<HTMLElement> = document.querySelectorAll('#navigation .subMenu');
                elems.forEach((elem: HTMLElement) => elem.classList.add('hidden'));

                // re-enable focus on menu item
                this.menuItems[this.focusedMenu].tabIndex = 0;
                this.menuItems[this.focusedMenu].focus();
            }
            // open submenu
            else if (type && !(event.target as HTMLElement).classList.contains('subMenuLink')) {
                // open submenu
                const elem: HTMLElement = (event.target as HTMLElement).querySelector('.subMenu') as HTMLElement;
                elem.classList.remove('hidden');

                // reset submenu options & set focus on 1st submenu item
                this.submenuItems = document.querySelectorAll('#navigation .mainMenu [tabindex="0"] .subMenu a') as NodeListOf<HTMLElement>;
                this.focusedSubmenu = 0;
                this.submenuItems[this.focusedSubmenu].focus();
            
                // disable focus on menu item
                (event.target as HTMLElement).tabIndex = -1;
            }
            // reset menu & follow link
            else this.ResetMenu();
        }

        MoveMenu(event: KeyboardEvent): void {
            // triggered from submenu for some reason
            if (!(event.target as HTMLElement).classList.contains('subMenuLink')) {
                event.preventDefault();
                const key: string = event.key;
                let elem: HTMLElement = (event.target as HTMLElement).querySelector('.subMenu') as HTMLElement;

                // Reset
                this.menuItems[this.focusedMenu].tabIndex = -1;
                // elem.classList.add('hidden');

                // Determine next Selected
                if (key === 'ArrowLeft') {
                    if (this.focusedMenu > 0) this.focusedMenu--;
                    else this.focusedMenu = (this.menuItems.length - 1);
                }
                else {
                    if (this.focusedMenu < (this.menuItems.length - 1)) this.focusedMenu++;
                    else this.focusedMenu = 0;
                }

                // Update
                this.menuItems[this.focusedMenu].tabIndex = 0;
                this.menuItems[this.focusedMenu].focus();

                // elem = document.querySelector('#navigation .mainMenu [tabindex="0"] .subMenu') as HTMLElement;
                // elem.classList.remove('hidden');
            }
        }

        MoveSubmenu(event: KeyboardEvent): void {
            // triggered from main menu for some reason
            if ((event.target as HTMLElement).classList.contains('subMenuLink')) {
                event.preventDefault();
                const key: string = event.key;

                // Determine next Selected
                if (key === 'ArrowUp') {
                    if (this.focusedSubmenu > 0) this.focusedSubmenu--;
                    else this.focusedSubmenu = (this.submenuItems.length - 1);
                }
                else {
                    if (this.focusedSubmenu < (this.submenuItems.length - 1)) this.focusedSubmenu++;
                    else this.focusedSubmenu = 0;
                }

                // Update
                this.submenuItems[this.focusedSubmenu].focus();
            }
        }

        ResetMenu(): void {
            this.menuItems[0].tabIndex = 0;
            this.focusedMenu = 0;
            this.focusedSubmenu = 0; 

            const elems: NodeListOf<HTMLElement> = document.querySelectorAll('#navigation .subMenu');
            elems.forEach((elem: HTMLElement) => elem.classList.add('hidden'));
        }
    };
</script>

<style scoped>
    #navigation {
        margin: 16px 0px;
        display: flex;
    }

    button {
        background-color: #f7f7f7;
        border: 1px solid #b9b9b9;
        cursor: pointer;
        height: 38px;
        width: 125px;
    }

    button:hover {
        background-color: #e9e9e9;
        border-color: #9f9f9f;
    }

    nav, #reset-btn {
        margin-left: 40px;
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

    .mainMenu li:hover, .mainMenu li:focus {
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

    .subMenu li:hover, .subMenu a:focus {
        background-color: #64b5f6;
    }

    .subMenu a {
        color: #000;
        height: 38px;
        text-decoration: none;
        width: 150px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .hidden {
        display: none;
    }

    @media (max-width: 750px) {
        #navigation {
            flex-direction: column;
        }

        nav {
            margin: 0px;
            width: 300px;
        }

        ul {
            margin: 10px 0px 0px 0px;
        }

        .subMenu {
            top: 28px;
        }

        #reset-btn {
            margin: 20px 0px 0px 0px;
        }
    }
</style>
