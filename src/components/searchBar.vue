<template>
    <div>
    <input type="text" class="searchBar" v-model="searchItem" placeholder="search..." required>
    <i class="fa fa-search btn" @click="sendData"></i>
    </div>
    
</template>

<script>
export default {
    name: 'SearchItem',
    data() {
        return {
            searchItem: ''
        }
    },
    methods: {
        sendData() {
            this.$emit('search', this.searchItem);
        }
    }
}   
</script>

<style scoped>
    .searchBar {
        border: none;
        border-bottom: 2px solid #C8CCD4;
        font-size: 22px;
        font-family: cursive;
        font-weight: 300;
        color: #205A9C;
        padding: 12px 0;
        text-align: center;
    }
    .searchBar:focus,
    .searchBar:active {
        border: none;
        outline: none;
    }

    .btn {
        display: inline-block;
        font-size: 22px;
        cursor: pointer;
        margin-left: 10px;
        padding: 0;
    }

    .btn:hover,
    .btn:active {
        font-size: 33px;
    }
    
</style>
