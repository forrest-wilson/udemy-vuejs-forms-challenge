<template>
    <span>{{ firstName }} {{ lastName }}</span>
</template>

<script>
export default {
    props: ["firstName", "lastName"]
}
</script>
