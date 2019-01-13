<template>
    <div>
        <div v-show="result">
            <a :href = "url + el.pageid" v-for = "el in pages" :key="el.pageid" >
                <div class="card">
                <p class="title">{{ el.title }}</p> 
                <p class="content">{{ el.extract }}</p>
                </div>
            </a>
        </div>
    </div>
</template>


<script>
export default {
    name: 'card',
    data() {
        return {
            url:  `http://en.wikipedia.org/?curid=`
        }
    },
    props: {
        pages: {
            required: true,
            type: Object
        },
        result: {
            required: true
        }
    }    
}
</script>


<style scoped>
    a {
       text-decoration: none; 
    }
    .card {
        width: 100%;
        background-color: #EEEEEE;
        margin: 15px 0;
    }

    .title {
        color: #205A9C;
        text-align: center;
        padding: 12px 18px;
        font-weight: 200;
    }

    .content {
        color: #000;
        font-weight: 200;
        padding: 0 8px 12px 8px;
    }
</style>
