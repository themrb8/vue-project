<script>
import SinglePost from  "../components/SinglePost.vue";

export default {
    name: "HomePage",
    components: {SinglePost},
    data() {
        return {
            posts: [
                {
                    id: 1,
                    title: 'Post 1',
                    fav: true,
                },
                {
                    id: 2,
                    title: 'Post 2',
                    fav: true,
                },
                {
                    id: 3,
                    title: 'Post 3',
                    fav: false,
                },
            ]
        }
    },
    computed: {
        favs() {
            return this.posts.filter(post => post.fav)
        },
        unFavs() {
            return this.posts.filter(post => !post.fav)
        },
        total() {
            return this.posts.length
        }
    },
    methods: {
        handleDelete(post) {
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        addPost() {
            this.posts.push({
                id: this.posts.length + 1,
                title: `Post ${this.posts.length + 1}`,
            })
        },
        handleFav(post) {
            this.posts = this.posts.map(p => {
                if(p.id === post.id){
                    p.fav = !p.fav
                }
                return p
            })
        }
    }
}
</script>

<template>
    <div class="container mx-auto ">
        <button class="mb-4 py-2 px-4 font-semibold rounded-lg text-white text-sm bg-orange-400" @click="addPost">Add Post</button>
        <h1 class="font-bold text-2xl mb-4">All: {{ total }}</h1>

        <single-post
        v-for="(post, index) in posts"
        :key="index"
        :post="post"
        @delete="handleDelete"
        @fav="handleFav"
        />
    </div>
    <div class="container mx-auto">
        <h1 class="font-bold text-2xl mb-4 mt-8">Unfavourite: {{ unFavs.length }}</h1>

        <single-post
        v-for="(post, index) in unFavs"
        :key="index"
        :post="post"
        @delete="handleDelete"
        @fav="handleFav"
        />
    </div>

    <div class="container mx-auto">
        <h1 class="font-bold text-2xl mb-4 mt-8">Favourite: {{ favs.length }}</h1>

        <single-post
        v-for="(post, index) in favs"
        :key="index"
        :post="post"
        @delete="handleDelete"
        @fav="handleFav"
        />
    </div>


    
</template>


<style scoped>

</style>