<template>
    <div>
        <h1>메모</h1>

        <table>
            <tr v-for="(memo, i) in memo" :key="i">
                <td>{{memo.id}}</td>
                <td>{{memo.writer}}</td>
                <td @click="$router.push(`/page/${memo.id}`)">{{memo.title}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    name:'MemoView',
    data() {
        return {
            memo:[]
        }
    },
    created() {
        this.$http.get('/api/memo')
        .then((response)=> {
            console.log(response.data);
            this.memo= response.data;
        })
    },
}
</script>