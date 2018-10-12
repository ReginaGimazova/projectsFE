<template>
    <div class="container">
        <h3 class="title">Library</h3>
        <div class="inside-container">
            <div class="box-left" id="box-left">
                <ul class="posts">
                    <li class="post-title"
                        v-for="post in posts"
                        v-on:click="selectedPost = post"
                        v-bind:class="{selected:post === selectedPost}"
                    >
                        {{post.title}}
                    </li>
                </ul>
            </div>
            <div class="box-right" id="box-right">
                <div
                        v-if="selectedPost"
                >
                    <h4>{{selectedPost.title}}</h4>
                    <p>
                        <a
                                v-for="cont in selectedPost.content"
                                v-bind:href="cont">{{cont}}</a>
                    </p>
                    <input type="button" value="Add content" v-on:click="addContent(selectedPost.id)">
                </div>

                <p
                    v-else>
                    Click on a post title
                </p>

            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "library",
        data(){
            return{
                posts: [
                    {
                        id: 1,
                        title: 'php',
                        content: ['http://php.net/']
                    },

                    {
                        id: 2,
                        title: 'js',
                        content: ['https://learn.javascript.ru/js']
                    },

                    {
                        id: 3,
                        title: 'java',
                        content: ['https://habr.com/hub/java/?mobile=no']
                    }
                ],

                selectedPost: null
            }
        },
        methods: {
            addNewTab: function () {
                this.tabs.push('next')
            },

            addContent: function (id) {
                let post = this.posts.filter(post => post.id === id).map(post => post.content);
                post.push('new link')
            }
        }
    }
</script>

<style scoped>
    .container {
        display: flex;
        flex-direction: column;
        align-items: inherit;
        justify-content: left;
    }

    .inside-container{
        display: flex;
        flex-direction: row;
        align-items: inherit;
        justify-content: left;
    }

    .title{
        margin-bottom: 15px;
        font-weight: lighter;
        text-align: center;
    }

    .box-left{
        display: flex;
        flex-wrap: wrap;
        flex-direction: column;
        width: 20%;
    }

    .box-right{
        margin-top: 10px;

    }

    .posts{
        list-style-type: none;
    }

    .post-title{
        font-size: 20px;
        padding: 10px;
        cursor: pointer;
    }
</style>