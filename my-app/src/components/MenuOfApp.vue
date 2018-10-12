<template>
    <div class="menu-app">
        <div class="menu-items">
            <a class="menu-item"
                v-for="tab in menuTabs"
                v-bind:class="{active: currentTab === tab}"
                v-on:click="func(tab)"
            >{{tab}}
            </a>
        </div>
    </div>
</template>

<script>
    export default {
        name: "MenuOfApp",
        data: () => {
            return{
                menuTabs: ['notes', 'library', 'something'],
                currentTab: 'notes'
            }
        },
        methods: {
            currentTabMenu() {
                this.$emit ('currentComponent', {
                    currentTab: this.currentTab.toLowerCase()
                })
            },

            func: function (tab) {
                this.currentTab = tab;
                this.currentTabMenu();
            }
        }
    }
</script>

<style scoped>
    .menu-app{
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: row;
        margin-bottom: 15px;
        background-color: black;
        padding: 5px;
    }

    .menu-items{
        display: flex;
        justify-content: space-around;
        width: 40%;
    }
    .menu-item{
        margin-right: 15px;
        color: #f9f8f6 !important;
        font-size: 18px;
        cursor: pointer;
    }
</style>