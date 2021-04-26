<template>
    <div class="description">
        <div class="top-header">
            <span>No description yet</span>
            <span>+ Add Description</span>
        </div>
        <div class="list">
            <ul class="details">
                <li v-for="d in data" :key="d">{{d}}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Description',
    computed: {
        data(){
            return this.$store.state.detail;
        }
    }
}
</script>

<style scoped>
::-webkit-scrollbar {
  width: 10px;
}
/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1; 
}
/* Handle */
::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 1em; 
}
/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555; 
}
.description {
    width: 25%;
    height: 35.8em;
    overflow-y: scroll;
}
.top-header {
    margin: 1em;
    padding: 1.5em;
    font-size: small;
    background: whitesmoke;
}
.top-header span:nth-child(2){
    margin-left: 1em;
    color: darkblue;
    cursor: pointer;
}
.list {
    margin: 1em;
}
.details {
    list-style-type: none;
    padding: 0;
    margin-left: 1em;
    text-align: left;
}
.details li {
    margin-top: 1em;
    color: blue;
    font-size: small;
}
</style>