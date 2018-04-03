<template>
    <div>
        <h2>{{msg}}</h2>
        <hr>
        <h3>{{count}}</h3>
        <button @click="$store.commit('add',10)">+</button>
        <button @click="reduce">-</button>
        <p>
            <button @click="addAction">+</button>
            <button @click="reduceAction">-</button>
        </p>
        <h3>{{$store.state.a.count}}</h3>
    </div>
</template>
<script>
    import store from '@/vuex/store'
    import {mapState,mapMutations,mapGetters, mapActions} from 'vuex'
    export default{
        data(){
            return{
                msg:'Hello vuex'
            }
        },
        store,
        // vuex向模板传值的方式一：
            // computed: {
            //     count(){
            //         return this.$store.state.count;
            //     }
            // },
        // vuex向模板传值的方式二：
            // computed:mapState({
            //     count:state=>state.count
            // })
        // vuex向模板传值的方式三：
        computed:{
            ...mapGetters(['count']),
            // count(){
            //     return this.$store.getters.count
            // }
        },
        // methods:mapMutations(['add','reduce'])
        methods:{
            ...mapMutations([
                'add','reduce'
            ]),
            ...mapActions(['addAction','reduceAction'])
        }
    }
</script>