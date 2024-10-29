<template lang="">
    <div class="news" v-if="news.length">
        <div class="btn">
            <button 
            v-for="tab in tabs" :key="tab.value"
            @click="tab.value === 'all' ? openApiAll() : openApi(tab.value)"
            :class="{active: tabActive === tab.value}">
            {{ tab.label }}
        </button>
        </div>
        <div class="newscard" v-for="(card, i) in news" :key="i">
            <figure><img :src="card.thumbnail_url"/></figure>
            <div class='txt'>
                <p>{{ card.published_at }}</p>
                <h3>{{ card.title }}</h3>
                <p>{{ card.publisher }} {{ card.author }}</p>
            </div>
            <!-- {{ news }} -->
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    props:["content"],
    data(){
        return{
            news: [],
            tabActive: 'all',
            tabs: [
                { value: 'all', label: '전체' },
                { value: 'politics', label: '정치' },
                { value: 'economy', label: '경제' },
                { value: 'society', label: '사회' },
                { value: 'culture', label: '문화' }
            ]
        };
    },
    created(){
        this.openApiAll()
    },
    methods: {
        async openApiAll(){
            const res = await axios.get(`https://server-ten-dusky.vercel.app/news?t=${this.content}`);
            this.news = res.data.data
            this.tabActive = 'all';
        },
        async openApi(c){
            const res = await axios.get(`https://server-ten-dusky.vercel.app/news/sec?t=${this.content}&s=${c}`);
            this.news = res.data.data
            this.tabActive = c;
        }
    },
}
</script>

<style lang="scss">
    .home,
    .about{
        justify-items: center;
    }
    .news{
        width: 843px;
    }
    .btn{
        button{
            border: 0;
            background-color: white;
            font-weight: bold;
            color: #2c3e50;
            &.active {
                color: #42b983;
            }
        }
    }
    .newscard{
        border: 1px solid #ddd;
        // border-bottom: 1px solid #ddd;
        // width: 200px;
        margin: 10px 0;
        padding: 10px;
        
        display: flex;
        justify-content: space-around;
        align-items: center;
        
        figure{
            margin: 0;
            width: 40%;
            img{width: 100%;}
        }
        .txt{
            width: 40%;
        }
    }
</style>