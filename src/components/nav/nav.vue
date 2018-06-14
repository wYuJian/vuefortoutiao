<script type="text/ecmascript-6">
import { Indicator } from 'mint-ui'
export default {
    name: 'Nav',
    props: ['navData'],
    data() {
        return {
            navIndex: 0
        }
    },
    render() {
        let nav = this.navData.showNav ? (
            <ul class="menuClass">
                {this.navData.showNav.map((item, index) => {
                    return (
                        <li
                            class={[
                                'nav-list-class ',
                                this.navIndex == index ? 'nav-active' : ''
                            ]}
                            key={index}
                            data-index={index}
                            onClick={this.changeNavIndex.bind(this,index)}
                        >
                            <span>{item}</span>
                        </li>
                    )
                })}
            </ul>
        ) : (
            ''
        )
        return (
            <div class="nav channel">
                <a href="">
                    <img src="https://s3.pstatp.com/toutiao/static/img/logo.201f80d.png" />
                </a>
                {nav}
            </div>
        )
    },
    components: {},
    created() {},
    methods: {
        changeNavIndex:function(index){
            this.navIndex = index;
            console.log(index)
        }
    }
}
</script>

<style scoped lang="less">
@import url(./nav.less);
</style>
