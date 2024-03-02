<template>
    <div>
        <h2 v-bind="$attrs">Article Info</h2>
        <h4>{{ name }}</h4>
        <h4>Likes - {{ likes }}</h4>
        <h4>Published - {{ isPublished ? 'Yes' : 'No' }}</h4>
    </div>
</template>

<script>
    export default {
        name: 'ArticleItem',
        props: {
            name: String,
            likes: Number,
            isPublished: Boolean
        },
        inheritAttrs: false
    }
</script>
