<template>
    <main>
        <section class="container">
            <h1>Vídeos</h1>

            <section class="videos">
                <a class="video" v-for="(video, index) in videos" :key="index" :href="video.link">
                    <img :src="video.thumb" :alt="video.title">
                    <div class="video-title">{{ video.title }}</div>
                    
                </a>

            </section>

        </section>
    </main>
</template>

<script>
import api from '@/services/api.js'

export default {
    name: 'Videos',
    data(){
        return{
            videos:[]
        }
    },
    mounted(){
        api.get('/videos.json').then(response => {
            this.videos = response.data;
        });
    }
}
</script>

<style scoped>
    main{
        align-items: center;
    }

    .video{
        width: 80%;
    }

    .video img{
        width: 100%;
    }

</style>
