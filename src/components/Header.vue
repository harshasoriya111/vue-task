<template>
    <div class="header">
        <div class="header-left">
            <button type="button" class="saved-list">
                <img alt="icon-list" src="@/assets/icon-list.png">
                <span>SAVED LISTS</span>
            </button>
            <div class="saved-filter">
                <img alt="filter" src="@/assets/filter.png">
                <span>SAVED FILTERS</span>
            </div>
            <div class="search-history">
                <img alt="history" src="@/assets/history.png">
                <span>SEARCH HISTORY</span>
            </div>
        </div>
        <div class="header-right">
            <input type="text" v-model="search" placeholder="Search" class="search-area">
        </div>
    </div>
</template>

<script>
export default {
    name: 'Header',
    computed: {
        search : {
            get(){
                return this.$store.state.search
            },
            set(value){
                this.$store.state.search = value
            }
        }
    }
}
</script>

<style scoped>
.header {
    padding: 1em;
    display: flex;
    background: whitesmoke;
}
.header-left {
    display: flex;
    width: 60%;
    align-items: center;
    font-size: 0.8em;
}
button.saved-list {
    padding: 0.5em 1em 0.5em 1em;
    width: 11em;
    background: #282A35;
    color: white;
    margin-right: 3em;
    cursor: pointer;
}
button.saved-list img, .saved-filter img, .search-history img{
    position: relative;
    top: 2px;
    padding-right: 1em;
}
.saved-filter {
    margin-right: 5em;
    cursor: pointer;
}
.search-history {
    cursor: pointer;
}
.header-right {
    width: 40%;
    text-align: left;
    align-items: center;
}
input.search-area {
    width: 96%;
    height: 2em;
    border: 1px solid lightgray;
    padding: 0em 1em 0em 1em;
}
</style>