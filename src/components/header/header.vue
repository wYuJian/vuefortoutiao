<script type="text/ecmascript-6">
import { Header } from 'mint-ui'
import Vue from 'vue'
Vue.component(Header.name, Header)
export default {
    name: 'Header',
    data() {
        return {
           
        }
    },
    render() {

        return (
            <div>
                <mt-header>
                    <mt-button  slot="left" class='line'>下载APP</mt-button>
                    <mt-button  slot="left">
                        <p>北京  雨 18°/28°▽ </p>
                    </mt-button>
                    <mt-button class='line'  slot="right">
                        侵权投诉
                    </mt-button>
                    <mt-button  slot="right">
                        头条产品
                    </mt-button>
                </mt-header>
            </div>
        )
    },
    components: {},
    mounted() {
        
    },
    methods: {
       
    }
}
</script>

<style scoped lang="less">
@import url('./header.less');
</style>
