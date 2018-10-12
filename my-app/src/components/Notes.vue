<template>
    <div class="container">
        <h3 class="title">Notes</h3>

        <div class="form-name">
            <input placeholder="write name of note" class="input-name" v-model="nameOfNote" />
        </div>

        <div class="form-note">
            <textarea class="note-text"
                    placeholder="write note"
                    v-model="note"
                    v-bind:maxLength="maxNote">
            </textarea>
        </div>

        <i class="prompt">Left to enter {{canEnterNote}} symbols</i>

        <button class="form-control" v-on:click="addNote()">Add note</button>

        <div class="note">
            <div  v-for="item in items">
                <div class="note-body">
<!--
                    <h5 class="title">Name of note</h5>
-->
                    <h5 class="title">{{item.nameOfNote}}</h5>

<!--
                    <h5 class="title">Text of note</h5>
-->
                    <p>{{item.note}}</p>
                </div>
                <button class="form-control" v-on:click="removeItem($index)">Delete</button>
            </div>

        </div>
    </div>
</template>

<script>
    export default {
        name: "notes",
        data() {
            return{
                nameOfNote: '',
                note: '',
                items: [],
                maxNote: 500
            }
        },
        computed: {
            canEnterNote: function () {
                return this.maxNote - this.note.length;
            },

            currentComponent: function () {
                return this.nameOfNote.toLowerCase();
            }
        },

        methods: {
            addNote:function () {
                this.items.push({
                    nameOfNote: this.nameOfNote,
                    note: this.note
                })
            },
            
            removeItem: function (index) {
                this.items.splice(index, 1)
            }
        }
    }
</script>

<style scoped>
    .prompt{
        margin-left: 10px;
    }

    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .title{
        margin-bottom: 15px;
        font-weight: lighter;
    }

    .form-name{
        display: flex;
        width: inherit;
        margin-bottom: 10px;
        justify-content: center;
    }

    .form-note{
        display: flex;
        width: inherit;
        justify-content: center;
    }
    .input-name{
        width: 70%;
    }

    .note-text{
        width: 70%;
    }

    .form-control{
        width: auto;
        margin-top: 10px;
    }

    .note{
        margin-top: 40px;
        border-top: 1px solid black;
        width: inherit;
        display: flex;
        flex-direction: column;
    }

</style>
