<template lang="">
    <div v-show="visibleSlide === index" class="container">
        <div class="content">
            <img :src="imgSource" :alt="title" class="poster-movie">
            <p class="movie-title">
                {{title}}
            </p>
        </div>
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

<style lang="scss" scoped>
@use "../styles/partials/mixins" as *;

div.container {
    position: relative;
    width: 300px;
    height: 450px;
    background-color: #0b0b0b74;
    border-radius: 10%;
    overflow: hidden;

    img {
        width: 10%;
    }
}

div.container::before {
    content: '';
    position: absolute;
    inset: -40px 70px;
    background: linear-gradient(#37f8ff7d, #ff400074);
    transition: 1s ease-in;
    animation: animate 4s linear infinite;

    
}

div.container:hover::before {
    inset: -40px -110px;
}

div.container::after {
	content: '';
	position: absolute;
	inset: 4px;
	background: #2a2a2a;
	border-radius: 10%;
	z-index: 1;
}

@keyframes animate {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
    div.content {
    position: absolute;
    inset: 12px;
    border: 6px solid #0b0b0b74;
    z-index: 2;
    border-radius: 10%;
    overflow: hidden;
    @include flex(row, center, center);
    
    }
    div.content img {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: .5s;
    }

    div.content img:hover {
        opacity: 0;
    }

    p.movie-title {
        color: #37f8ff7d;
        font-size: 1.5rem;
        text-align: center;
        padding: 1rem;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif

    }
</style>