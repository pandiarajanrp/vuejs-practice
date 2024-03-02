<template>
    <h2>
        Welcome {{name}} a.k.a {{ heroName }}
    </h2>
</template>

<script>
    export default {
        name: 'GreetItem',
        props: ['name', 'heroName']
    }
</script>
