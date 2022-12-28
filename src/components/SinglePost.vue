<script>
export default {
    name: "SinglePost",
    props: ['post'],
    methods: {
        handleClick(post) {
            this.$emit('delete', post);
        },
    }
}
</script>

<template>
    <div class="container mx-auto">
        <div class="flex justify-between items-center w-half bg-slate-300 p-2 rounded-lg mb-2 h-full">
            <h3 :class="{'fav' : post.fav}" class="text-xl font-semibold ">{{ post.title }}</h3>
            <button class="bg-red-500 p-2 rounded-lg text-white ml-auto mr-4" @click="handleClick(post)">Delete</button>
            <button class="bg-blue-500 p-2 rounded-lg text-white" @click="$emit('fav', post)">Favourite</button>
        </div>
    </div>
</template>

<script scoped>
</script>