<template lang="">
    <div v-show="visibleSlide === index">
        <p>
            {{title}}
        </p>
        <img :src="imgSource" :alt="title">
    </div>
    
</template>

<script>
export default {
    props: {
        visibleSlide: {
            type: Number,
            required: true
        },

        index: {
            type: Number,
            required: true
        },

        title: {
            type: String,
            requierd: true
        },

        imgSource: {
            type: String,
            requierd: true
        }
    }
}
</script>

<style lang="">
    
</style>