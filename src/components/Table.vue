<template>
    <div class="table-list">
        <table>
            <tr class="row">
                <th class="col one">Date</th>
                <th class="col two">List Name</th>
                <th class="col three">No. of Entities</th>
                <th class="col four">Actions</th>
                <th class="col five"></th>
            </tr>
            <tr v-for="info in filteredInfos" :key="info.id" class="row">
                <td v-if="info.date==''" class="data one">&#9851;</td>
                <td v-else class="data one">{{info.date}}</td>
                <td class="data two" :class="{sps : info.date==''}">{{info.listName}}</td>
                <td class="data three">{{info.entities}}</td>
                <td class="data four">
                    <img alt="envelope" src="@/assets/envelope.png">
                    <img v-show="info.date!=''" alt="share" src="@/assets/share.png">
                    <img v-show="info.date!=''" alt="pen" src="@/assets/pen.png">
                    <img v-show="info.date!=''" alt="trash" src="@/assets/trash.png">
                </td>
                <td class="data five">
                    <button type="button" class="btn" @click="showDetail(info.description)">Details</button>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    name: 'Table',
    props: {
        infos: Array
    },
    computed: {
        filteredInfos: function(){
            return this.infos.filter((info) => {
                return info.listName.toLowerCase().match(this.$store.state.search)
            });
        }
    },
    methods: {
        showDetail(temp) {
            this.$store.state.detail = temp
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
.table-list {
    width: 75%;
    height: 35.8em;
    overflow-y: scroll;
}
table {
    width: 97%;
    border-collapse: collapse;
}
.row {
    font-size: small;
    border-bottom: 1px solid whitesmoke;
    color: grey;
}
.row:hover{
    background: whitesmoke;
}
.col {
    padding: 1em;
}
.col.one {
    width: 15%;
}
.col.two {
    text-align: left;
}
.col.three {
    width: 13%;
}
.col.four {
    width: 20%;
    text-align: left;
}
.col.five {
    width: 10%;
}
.data {
    padding: 1.5em;
}
.data.one {
    color: lightgray;
}
.data.two {
    font-weight: bold;
    color: black;
    text-align: left;
}
.data.two.sps {
    color: deepskyblue;
}
.data.three {
    color: black;
    text-align: right;
}
.data.four {
    text-align: left;
}
.data.four img {
    margin-right: 1em;
}
.btn {
    background: white;
    border: none;
    color: darkblue;
    cursor: pointer;
}
.btn:hover{
    font-weight: bold;
    border-bottom: 2px solid darkblue;
}
</style>